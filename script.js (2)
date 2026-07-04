document.addEventListener('DOMContentLoaded', () => {
    const cityinput = document.getElementById('city-input')

    const getweather = document.getElementById('get-weather')

    const cityname = document.getElementById('city-name')

    const weatherinfo = document.getElementById('weather-info')

    const temperature = document.getElementById('temperature')

    const description = document.getElementById('description')

    const errormsg = document.getElementById('error-msg')

    const API_KEY = "8a0fb52968fae642b0348b645afa0da4"

    getweather.addEventListener('click', async () => {
        const city = cityinput.value.trim()

        if(!city) return

        try {
            const weatherdata = await fetchweatherdata(city)
            displayweatherdata(weatherdata)
        } catch (error) {
            showerror()
            
        }

        async function fetchweatherdata(city){
            const url = `https://api.openweathermap.org/data/2.5/weather?q=${city}&units=metric&appid=${API_KEY}`;

            const response = await fetch(url)

            console.log(typeof response);
            
            console.log("response" , response);

            if(!response.ok) {
                throw new Error("city not found")
            }

            const data = await response.json()
            return data
            
            

        }

        function displayweatherdata(data){
            console.log(data);

            const {name , main , weather} = data 

            cityname.textContent = name

            temperature.textContent = `temperature: ${main.temp}`

            description.textContent = `weather: ${weather[0].description}`

            

            weatherinfo.classList.remove('hidden')
            errormsg.classList.add('hidden')

        }

        function showerror(){
            weatherinfo.classList.add('hidden')
            errormsg.classList.remove('hidden')



        }
    })
})