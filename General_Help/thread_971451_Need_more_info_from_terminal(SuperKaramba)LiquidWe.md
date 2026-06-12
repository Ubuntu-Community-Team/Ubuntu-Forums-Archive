---
title: "Need more info from terminal?(SuperKaramba)LiquidWeather slow data load."
date: 2008-11-05
forum: General Help
---

### Post by HousieMousie2 on 2008-11-05
LiquidWeather started acting up last night, after performing perfectly (for over a month) since I set up this new installation of Hardy Heron... I will likely be sticking with LTS releases.

There have been updates, but nothing jumped out at me for being related to: SuperKaramba, ImageMagic, PY-QT.  Though I may have missed something... brain death is a terrible thing.  ((WAY off topic... how to make Adept/Konsole/Any-Other-App give me the update/upgrade history?))

On to the issue at hand...

LiquidWeather suddenly takes too long to update weather data (averaging 3 minutes.)

I am not getting delays when connecting to Weather.Com via a web browser.  I am not using a proxy.  I have read many other web pages/posts that state that the SyntaxWarning is irrelevant.

```
<MyUserName>@<MyComputer'sName>:~$ superkaramba /home/<MyUserName>/Programs/LiquidWeather/lwp-15.0.skz
/home/<MyUserName>/Programs/LiquidWeather/lwp-15.0.skz/liquid_weather.py:3656: SyntaxWarning: import * only allowed at module level
sys.path.insert(0, '/home/<MyUserName>/Programs/LiquidWeather/lwp-15.0.skz')
Reading config
Reading from Config ...
fontSizeMatrix:
[20, 12, 10, 12, 10]
/home/<MyUserName>/Programs/LiquidWeather/Backgrounds//Clear (Raised)/bg.png
No such application: 'kxdocker'
Downloading weather in initWidget
http://xoap.weather.com/weather/local/<MyZipCode>?cc=*&dayf=5&par=<ABunchOfNumbers>&key=<MoreNumbers>
using weather.com
parsing XML
10:06
10
06
PM
dnamobst: 0
unit: mph
22
06
unit: kph
Observation:  ( @<MyLocation>, 22:06 CST Tue 4 Nov 08 )
  ( with 0 forecasts )
  icon            : 33
  sky             : Fair
  temperature     : 18&#65533;C
  relative_heat   : 18&#65533;C
  dewpoint        : 12&#65533;C
  visibility      : 16 km
  uv              : 0
  pollution       : 0
  wind            : SSE
  wind_speed      : 27 kph
  reverse_wind_arrows : 0
  wind_icon       : medium/SSE.png
  humidity        : 64 %
  pressure        : 1012
  pressure_change : falling
  cloud_cover     : 0 %
+++++++++++++++++++Today's Forecast++++++++++++++++++++++++
unit: kph
Forecast:  Tue ( date=Nov 4 )
  icon            : 44
  sky             : N/a
  temperature_low : 15&#65533;C
  temperature_high: 0&#65533;C
  uv              : N/A
  pollution       : 0
  wind_speed      : 0 kph
  wind            : Calm
  humidity        : 0 %
  rain            : 10 %
  pressure        : 0
  pressure_change : N/A
  sunrise         : N/A
  sunset          : N/A
unit: kph
Forecast:  Wed ( date=Nov 5 )
  icon            : 24
  sky             : Sunny / wind
  temperature_low : 7&#65533;C
  temperature_high: 26&#65533;C
  uv              : N/A
  pollution       : 0
  wind_speed      : 0 kph
  wind            : Calm
  humidity        : 0 %
  rain            : 10 %
  pressure        : 0
  pressure_change : N/A
  sunrise         : N/A
  sunset          : N/A
unit: kph
Forecast:  Thu ( date=Nov 6 )
  icon            : 32
  sky             : Sunny
  temperature_low : 3&#65533;C
  temperature_high: 20&#65533;C
  uv              : N/A
  pollution       : 0
  wind_speed      : 0 kph
  wind            : Calm
  humidity        : 0 %
  rain            : 0 %
  pressure        : 0
  pressure_change : N/A
  sunrise         : N/A
  sunset          : N/A
unit: kph
Forecast:  Fri ( date=Nov 7 )
  icon            : 32
  sky             : Sunny
  temperature_low : 4&#65533;C
  temperature_high: 21&#65533;C
  uv              : N/A
  pollution       : 0
  wind_speed      : 0 kph
  wind            : Calm
  humidity        : 0 %
  rain            : 0 %
  pressure        : 0
  pressure_change : N/A
  sunrise         : N/A
  sunset          : N/A
unit: kph
Forecast:  Sat ( date=Nov 8 )
  icon            : 32
  sky             : Sunny
  temperature_low : 7&#65533;C
  temperature_high: 23&#65533;C
  uv              : N/A
  pollution       : 0
  wind_speed      : 0 kph
  wind            : Calm
  humidity        : 0 %
  rain            : 0 %
  pressure        : 0
  pressure_change : N/A
  sunrise         : N/A
  sunset          : N/A
unit: mph
unit: mph
unit: mph
unit: mph
unit: mph
unit: mph
unit: mph
unit: mph
unit: mph
unit: mph
unit: mph
unit: mph

```
This is where it hangs up.  On the first start-up/data fetch, it  eventually goes on to say:
```
Cities for config menu:
['<MyLocation> (weather.com)']
29.88
unit: kph
22
47
```
On subsequent data fetch updates, (asking it to fetch) it says:
```
No such application: 'kxdocker'
Reading from Config ...
fontSizeMatrix:
[20, 12, 10, 12, 10]
/home/<My UserName>/Programs/LiquidWeather/Backgrounds//Clear (Raised)/bg.png
unit: kph
23
12
No such application: 'kxdocker'
>>>>>>>>>>>>>>>>>>>>> Widget Reset <<<<<<<<<<<<<<<<<<<<<<<<
/home/<MyUserName/.superkaramba/lwp/latest
15.0
Version Check:  Update message already shown
Version Check:  This is the latest version

```

It is not now, nor has my LW ever been configured to use kxdocker... not really planning on it since kxdocker has been dropped as a project and is not in the standard repositories... and has never been installed on my machine.

I have seen many others list a similar output, complete with the multiple "unit: mph" entries.  I could be wrong of course, but I don't think it is the issue and I have tried changing the LW setting to use metric units, but is has no effect on the output.


The above information was posted on the off chance someone else has had the same problem, knows a solution and is willing to share.  It is also posted in the hope that I will find a solution, can post it here, for the benefit of someone else encountering the same issue.

What I am really after is what I need to add to the command line "superkaramba /home/<MyUserName>/Programs/LiquidWeather/lwp-15.0.skz" to make it tell me what it is doing while it seems to be doing nothing at all... so that I might be able to figure out how to fix it... or at the very least, where to go from here in my searching.

I most sincerely thank you for your time!

---

### Post by HousieMousie2 on 2008-11-05
Well, after a while of long update times... this afternoon it decided to start updating quickly again... of course, it chose to change the selected location to display. Which is very strange, since I had deleted all but one location.

Oh well.

I would still like to know how to get more info out of the terminal... for future use.

---

