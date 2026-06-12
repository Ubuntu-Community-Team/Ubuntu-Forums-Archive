---
title: "Conky Customisation"
date: 2008-11-26
forum: General Help
---

### Post by b3n0 on 2008-11-26
Hey all,
I'm looking to customise conky a bit.
[IMG]http://fc72.deviantart.com/fs38/f/2008/331/8/e/SCR004_by_B3N0.jpg
I would like the display to be pushed to the right of the red line.
Where the blue arrow is, I would like the month.
Finally the green box, I would like it to be able to pick up my weather for Brisbane, Australia, in degrees celsius.
Thanks in advanced.
I've followed this tut. Including the parts about the weather, Brisbane is ASXX0016. As you can see I've copied the tut to a tea even down to the
desktop image.
[http://www.quicktweaks.com/2008/09/27/gmail-weather-beauty-right-on-your-ubuntu-desktop/]("http://www.quicktweaks.com/2008/09/27/gmail-weather-beauty-right-on-your-ubuntu-desktop/")

---

### Post by Bruce M. on 2008-11-27
> **b3n0 said:**
> Hey all,
I'm looking to customise conky a bit.

I would like the display to be pushed to the right of the red line.

Get rid of the email "Subjects".  That's what is pushing your conky to the left. Just show the number of new emails.  That alone should put your conky right of the red line.

> **b3n0 said:**
> Where the blue arrow is, I would like the month.
```

TEXT
24 hour time: ${time %H:%M:%S}
Short month: ${time %h} - Long Month ${time %B}
Short Day: ${time %a} - Long Day: ${time %A}
Short Year: ${time %y} - Long Year: ${time %Y}

All: ${time %a, %d. %h. %y }
or: ${time %A, %d, %B %Y }

All of it (12 hr. clock): ${time %c}

12 hour clock: ${time %r}
${time %R}
```
see attached!

> **b3n0 said:**
> Finally the green box, I would like it to be able to pick up my weather for Brisbane, Australia, in degrees celsius.

Show me your script for your weather. And I'll see what I can do for you.

**EDIT:** Better yet, take a look at [Kaivalagi's Python Scripts]("http://ubuntuforums.org/showthread.php?p=6097476") - weather, email and more and each of them is supported right here in the Ubuntu Forums in their proper thread by the author and others who use them.

Also take a look at [Post your .conkyrc files w/ screenshots]("http://ubuntuforums.org/showthread.php?t=281865"), you'll have more people helping you than you could possibly imagine.

My latest screen-shot shows 3 of Kaivalagi's Scripts: Email, Weather and GoogleCalendar (Agenda):

[center][[IMG]http://img368.imageshack.us/img368/8650/screenshotnt4.th.gif[/IMG]](http://img368.imageshack.us/my.php?image=screenshotnt4.gif)[/center]

CHIMO!
Have a nice day.
Bruce

---

### Post by b3n0 on 2008-11-27
Hey, thanks for your help.
Heres my weather script
```
# # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # #
#															#
# Pogodynka 0.2.2.1													#
#															#
# azhag (azhag@bsd.miki.eu.org)												#
#															# 
# # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # #
#															#
# Skrypt pobiera informacje o stanie pogody ze strony weather.yahoo.com dla danego miasta, nastêpnie formatuje je i	#
# wy¶wietla na ekranie. Skrypt mo¿e byæ wykorzystany np. w conky'm, xosd, *message.					#
#															#
# # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # #
#															#
# Wymagane aplikacje:													#
# w3m - tekstowa przegl±darka www											#
#															#
# # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # #
#															# 
# Przed u¿yciem skryptu nale¿y ustaliæ zmienne "sciezka" oraz "kod".							#
#															#
# Aby ustaliæ kod swojego miasta wejd¿ na stronê http://weather.yahoo.com/ i wyszukaj tam swoje miasto. Kodem jest 	#
# koñcówka linka z pogod± naszego miasta.										#	
#															#
# Przyk³adowe kody:													#
# Warszawa - PLXX0028													#
# Kraków - PLXX0012													#
# Gdañsk - PLXX0005													#
# Szczecin - PLXX0025													#
#															#
# Informacjê jak± wy¶wietla skrypt mo¿na zmieniæ haszuj±c odpowiednie linijki w sekcji "formatowanie informacji		#
# wyj¶ciowej". Mo¿na równie¿ w ³atwy sposób sformatowaæ w³asny wynik u¿ywaj±c dostepnych zmiennych.			#
#															#
# # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # #

#!/bin/bash

# Katalog, w którym znajduje siê skrypt
sciezka=~/scripts

# Kod miasta
kod=ASXX0016

plik=~/weather
# sprawdzenie czy serwer jest dostêpny
#if [ `ping -c1 216.109.126.70 | grep from | wc -l` -eq 0 ]
 # then
	#echo "Serwis niedostêpny"
  #else
	# pobieranie informacji
 	w3m -dump http://weather.yahoo.com/forecast/"$kod"_c.html | grep -A21 “Current” | sed ’s/DEG/°/g’ > $plik
	# ustalenie warto¶ci zmiennych
	stan=`head -n3 $plik | tail -n1`
	temp=`tail -n1 $plik | awk '{print $1}'`
	tempo=`head -n6 $plik | tail -n1`
	cisn=`head -n8 $plik | tail -n1`
	wiatr=`head -n16 $plik | tail -n1`
	wilg=`head -n10 $plik | tail -n1`
	wsch=`head -n18 $plik | tail -n1`
	zach=`head -n20 $plik | tail -n1`
	if [ `cat "$sciezka"/pogodynka.sh | grep -x "# $stan" | wc -l` -eq 0 ]
	  then
		stanpl=$stan
	  else
		stanpl=`cat "$sciezka"/pogodynka.sh | grep -xA1 "# $stan" | tail -n1 | awk '{print $2,$3,$4,$5,$6,$7}'`
	fi
	
	# formatowanie informacji wyj¶ciowej
	# dostêpne zmienne:
	# $stan		opis stanu po angielsku
	# $stanpl	opis stanu po polsku
	# $temp		temperatura powietrza
	# $tempo	temperatura odczuwalna
	# $cisn		ci¶nienie atmosferyczne
	# $wiatr	kierunek, si³a wiatru
	# $wilg		wilgotno¶æ powietrza
	# $wsch		godzina wschodu s³oñca
	# $zach		godzina zachodu s³oñca
	
	#echo $stan
	#echo $stanpl
	echo $temp F  /  $tempo F
	#echo Cisnienie $cisn hPa
	#echo $wiatr
	#echo Wilgotno¶æ: $wilg
	#echo Wschód S³oñca: $wsch
	#echo Zachód S³oñca: $zach
	#echo $stanpl, $temp C

#fi

# # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # # #
#
# T³umaczenia stanów pogody.
# Je¿eli zauwa¿ysz pogodê, której nie ma jeszcze na liscie daj mi znaæ na maila podanego na górze. Z góry dziêkujê.
#
# Sunny
# S³onecznie
# Clear
# Przejrzy¶cie
# Fair
# Pogodnie
# Sunny/Windy
# S³onecznie/Wiatr
# Clear/Windy
# Przejrzy¶cie/Wiatr
# Fair/Windy
# Przejrzy¶cie/Wiatr
# Windy
# Wiatr
#
# Partly Cloudy
# Czê¶ciowo pochmurnie
# Partly Cloudy and Windy
# Czê¶ciowo pochmurnie/Wiatr
# Partly Sunny
# Czê¶ciowo s³onecznie
# Mostly Clear
# Przew. przejrzy¶cie
# Partly Sunny/Windy
# Czê¶ciowo s³onecznie/Wiatr
# Mostly Clear/Windy
# Przew. przejrzy¶cie/Wiatr
# Mostly Sunny
# Przew. p³onecznie
# Mostly Sunny/Windy
# Przew. s³onecznie/Wiatr
# Scattered Clouds
# Rzadkie ob³oki
#
# Cloudy
# Pochmurnie
# Overcast
# Ca³k. zachmurzenie
# Cloudy/Windy
# Pochmurnie/Wiatr
# Overcast/Windy
# Ca³k. zachmurzenie/Wiatr
# Mostly Cloudy/Windy
# Przew. pochmurnie/Wiatr
# Mostly Cloudy
# Przew. pochmurnie
# Am Clouds / Pm Sun
# Ranek pochmurny/S³oneczne popo³udnie
#
# Light Drizzle
# Lekka m¿awka
# Drizzle
# M¿awka
# Light Rain
# Lekki deszcz
# Rain
# Deszcz
# Heavy Rain
# Ulewa
# Light Rain/Fog
# Lekki deszcz/Mg³a
# Rain/Fog
# Deszcz/Mg³a
# Light Drizzle/Windy
# Lekka m¿awka/Wiatr
# Drizzle/Windy
# M¿awka/Wiatr
# Light Rain/Windy
# Lekki deszcz/Wiatr
# Rain/Windy
# Deszcz/Wiatr
# Rain / Wind
# Deszcz/Wiatr
# Heavy Rain/Windy
# Ulewa/Wiatr
# AM Light Rain
# Ranny lekki deszcz
# PM Light Rain
# Popo³udniowy lekki deszcz
# Pm Light Rain
# Popo³udniowy lekki deszcz
# AM Light Rain/Windy
# Ranny lekki deszcz/Wiatr
# PM Light Rain/Windy
# Popo³udniowy lekki deszcz/Wiatr
#
# Rain Shower
# Przelotny deszcz
# Shower
# Przelotna ulewa
# Showers
# Przelotna ulewa
# Heavy Rain Shower
# Mocna ulewa
# Heavy Rain Shower/Windy
# Mocna ulewa/Wiatr
# Light Rain Shower
# Lekka ulewa
# AM Shower
# Poranna ulewa
# AM Showers
# Poranna ulewa
# Am Showers
# Poranna ulewa
# AM Showers / Wind
# Poranna ulewa/Wiatr
# PM Shower
# Popo³udniowa ulewa
# PM Showers / Wind
# Popo³udniowe ulewy/Wiatr
# Few Showers / Wind
# Przelotne deszcze/Wiatr
# Showers / Wind
# Deszcze/Wiatr
# PM Showers
# Popo³udniowe ulewy
# Pm Showers
# Popo³udniowe ulewy
# Scattered Shower
# Rozleg³a ulewa
# Scattered Showers
# Rozleg³e ulewy
# Scatter Showers
# Rozleg³e ulewy
# Rain Shower/Windy
# Przelotny deszcz/Wiatr
# Shower/Windy
# Przelotna ulewa/Wiatr
# Light Rain Shower/Windy
# Lekka ulewa/Wiatr
# AM Shower/Windy
# Poranna ulewa/Wiatr
# PM Shower/Windy
# Popo³udniowa ulewa/Wiatr
# Scattered Shower/Windy
# Rozleg³a ulewa/Wiatr
# Scatter Showers / Wind
# Rozleg³e ulewy/Wiatr
# Few Showers
# Mo¿liwe ulewy
# Few Showers/Windy
# Mo¿liwe ulewy/Wiatr
# Showers in the Vicinity
# Pobliskie ulewy
#
# Light Snow
# Lekki ¶nieg
# Snow
# Šnieg
# Snow / Wind
# Šnieg/Wiatr
# Heavy Snow
# Mocny ¶nieg
# Light Snow Pellets
# Lekki grad ¶nie¿ny
# Snow Pellets
# Grad ¶nie¿ny
# Light Ice Pellets
# Lekki grad lodowy
# Ice Pellets
# Grad lodowy
# Wintery Weather
# Zimowa pogoda
# Light Freezing Rain
# Lekki zamarzaj±y deszcz
# Freezing Rain
# Zamarzaj±cy deszcz
# Flurries/Windy
# Zamiecie/Wiatr
# Light Flurries/Windy
# Lekkie zamiecie/Wiatr
# Light Snow/Windy
# Lekki ¶nieg/Wiatr
# Light Snow / Wind
# Lekki ¶nieg/Wiatr
# Snow/Windy
# Šnieg/Wiatr
# Heavy Snow/Windy
# Mocny ¶nieg/Wiatr
# Light Snow Pellets/Windy
# Lekki grad ¶nie¿ny/Wiatr
# Snow Pellets/Windy
# Grad ¶nie¿ny/Wiatr
# Light Ice Pellets/Windy
# Lekki grad lodowy/Wiatr
# Ice Pellets/Windy
# Grad lodowy/Wiatr
# Light Freezing Rain/Windy
# Lekki zamarzaj±cy deszcz/Wiatr
# Freezing Rain/Windy
# Zamarzaj±cy deszcz/Wiatr
# Wintery Mix
# Miks zimowy
# Light Snow Grains
# Lekkie granulki ¶niegu
# Snow Grains
# Granulki ¶niegu
# Rain/Snow
# Šnieg z deszczem
# Rain / Snow Showers
# Deszcz ze ¶niegiem
# Rain / Snow
# Deszcz ze ¶niegiem
# Rain / Thunder
# Deszcz / Burza
# Rain/Show/Windy
# Šnieg z deszczem/Wiatr
# Rain / Snow / Wind
# Šnieg z deszczem/Wiatr
# Light Rain/Freezing Rain
# Lekki deszcz/Zamarzaj±cy deszcz
# Rain/Freezing Rain
# Deszcz/Zamarzaj±cy deszcz
# Light Rain/Freezing Rain/Windy
# Lekki deszcz/Zamarzaj±cy Deszcz/Wiatr
# Rain/Freezing Rain/Windy
# Deszcz/Zamarzaj±cy deszcz/Wiatr
# AM Snow
# Poranny ¶nieg
# PM Snow
# Popo³udniowy ¶nieg
# AM Light Snow
# Poranny lekki ¶nieg
# PM Light Snow
# Popo³udniowy lekki ¶nieg
# Ice Crystals
# Kryszta³ki lodu
# Ice Crystals/Windy
# Kryszta³ki lodu/Wiatr
# 
# Snow Showers
# Burze ¶nie¿ne
# Snow Shower
# Burza ¶nie¿na
# Heavy Snow Shower
# Mocna burza ¶nie¿na
# Heavy Snow Shower/Windy
# Mocna burza ¶nie¿na/Wiatr
# PM Snow Showers
# Popo³udniowe burze ¶nie¿ne
# AM Snow Showers
# Poranne burze ¶nie¿ne
# Rain/Snow Showers
# Deszcz/Burze ¶nie¿ne
# Snow Showers/Windy
# Burze ¶nie¿ne/Wiatr
# PM Snow Showers/Windy
# Popo³udniowe burze ¶nie¿ne/Wiatr
# AM Snow Showers/Windy
# Poranne burze ¶nie¿ne/Wiatr
# Rain/Snow Showers/Windy
# Deszcz/Burze ¶nie¿ne/Wiatr
# Light Snow Showers
# Lekkie burze ¶nie¿ne
# Light Snow Shower
# Lekka burza ¶nie¿na
# Light Snow Showers/Windy
# Lekkie burze ¶nie¿ne/Wiatr
# Flurries
# Zamiecie
# Light Flurries
# Lekkie zamiecie
# Scattered Flurries
# Rozleg³e zamiecie
# Few Flurries
# Mo¿liwe zamiecie
# Few Flurries/Windy
# Mo¿liwe zamiecie/Wiatr
# Scattered Snow Showers
# Rozleg³e burze ¶nie¿ne
# Scattered Snow Showers/Windy
# Rozleg³e burze ¶nie¿ne/Wiatr
# Few Snow Showers
# Mo¿liwe burze ¶nie¿ne
# Few Snow Showers/Windy
# Mo¿liwe burze ¶nie¿ne/Wiatr
# Freezing Drizzle
# Marzn±ca m¿awka
# Light Freezing Drizzle
# Lekka marzn±ca m¿awka
# Freezing Drizzle/Windy
# Marzn±ca m¿awka/Wiatr
# Light Freezing Drizzle/Windy
# Lekka marzn±ca m¿awka/Wiatr
# Drifting Snow
# Zawieja ¶nie¿na
# 
# Thunderstorms
# Burze
# T-storms
# Burze
# T-Storms
# Burze
# T-Storm
# Burza
# Scattered Thunderstorms
# Rozleg³e burze
# Scattered T-Storms
# Rozleg³e burze
# Thunderstorms/Windy
# Burze/Wiatr
# Scattered Thunderstorms/Windy
# Rozleg³e burze/Wiatr
# Rain/Thunder
# Deszcz/Grzmoty
# Light Thunderstorms/Rain
# Lekkie burze/Deszcz
# Thunderstorms/Rain
# Burze/Deszcz
# Light Rain with Thunder
# Lekki deszcz z grzmotami
# Rain with Thunder
# Deszcz z grzmotami
# Thunder in the Vicinity
# Pobliskie burze
# 
# Fog
# Mg³a
# Haze
# Lekka mg³a
# Mist
# Lekkie zamglenie
# Fog/Windy
# Mg³a/Wiatr
# Haze/Windy
# Lekka Mg³a/Wiatr
# Mist/Windy
# Lekkie zamglenie/Wiatr
# Partial Fog
# Czê¶ciowa mg³a
# Smoke
# Gêsta mg³a
# Foggy
# Mglisto
# AM Fog/PM Sun
# Ranna mg³a/Popo³udniowe s³oñce
# Shallow Fog
# P³ytka mg³a
# 
# Blowing Dust
# Zawieja py³owa
# Blowing Sand
# Zawieja piaskowa
# Duststorm
# Burza piaskowa
# Wind
# Wiatr
# Widespread Dust/Windy
# Rozleg³e zamiecie/Wiatr
# Widespread Dust
# Rozleg³e zamiecie
# Low Drifting Sand
# Zawieja piaskowa
# 
# Data Not Available
# Dane niedostêpne
# N/A
# N/D
# N/a
# N/d

```

Where can I find the conky config file?

thanks

---

### Post by Bruce M. on 2008-11-27
> **b3n0 said:**
> Hey, thanks for your help.
Heres my weather script

Hi b3n0,

Actually, after posting my reply I checked out where you got your conky from and saw that script in the downloaded file.  Didn't understand much as it's not in English (and I'm not a programmer) however I did notice two things, It uses Yahoo Weather and Yahoo uses Weather.com to get it's data. Kind of a round-about way of doing it, but that's how the author of the script did it. Kaivalagi's Weather Forecast script uses weather.com direct and defaults to °C not °F

So, two suggestions:
[LIST=1]
[*]Ask the author at the site where you got the scripts how to:
[LIST]
[*]delete the subject headings from the mail script and,
[/LIST]
[*]Create your own conky file (or modify the one you have) and use Kaivalagi's Scripts to get support here at the Ubuntu Forums:
[LIST]
[*][Conky Weather Forecast Python Script]("http://ubuntuforums.org/showthread.php?t=869328")
[*][Conky SSL Email Python Script]("http://ubuntuforums.org/showthread.php?t=869771")
[/LIST]
[/LIST]

If you want to continue using the weather script you have:


1. Open **pogodynka.sh** file look for this line kod=USID0025. Replace USID0025 with the location ID you got from step 10

2. If you want the temperature in Celsius instead of Fahrenheit, find the following line:
```
w3m -dump http://weather.yahoo.com/forecast**/"$kod".html |** grep -A21 "Current" | sed 's/DEG/°/g' > $plik
```
and replace it with:
```
w3m -dump http://weather.yahoo.com/forecast**/"$kod"_c.html |** grep -A21 “Current” | sed ’s/DEG/°/g’ > $plik
```
[/LIST]

> **b3n0 said:**
> Where can I find the conky config file?

thanks

According to the instructions at the site you gave as an example:
> 6. Open .conkyrc file. Look for this line:
It is a hidden file in your home directory:

To edit it open a terminal: copy and paste this line:
```
gedit ~/.conkyrc
```
Replace **gedit** with **mousepad** (Xubuntu) or **kate** (Kubuntu).

The site where you got your conky from is a nice setup, but doesn't explain how to "customize" conky for your own needs/wants/desires. It only explains how to use "his" setup.

All of Kaivalagi's Scripts are customizable and in each thread (each script has it's own thread) there are Ubuntu people willing to help you.

Why am I mentioning Kaivalagi's Scripts so much? Two reasons:
[LIST=1]
[*]He's a programmer by trade.
[*]He is actively involved in supporting all of his scripts right here in the Ubuntu Forums.
[*]His weather script is multi-lingual (see my screenshot, it's in Spanish).
[*]I've been using his scripts from the beginning and I know they "just work"
[/LIST]

Also, there are others from Australia using his scripts. :D

Any more questions just ask.
Have a nice day.
Bruce

---

### Post by b3n0 on 2008-11-27
Thanks once again for your help. I'm going to remove conky and start again following the tools you have given me.
I completely agree, the tut I was following left me clouded and clueless, usually when I follow tuts I actually learn stuff. By the end of the tutorial I had no idea what I had done/changed or what any of the scripting meant.
 
Is it too much to ask for some help removing it so I can start fresh. As I'm still very fresh with my commands. Also I had a look for that .conkyrc file the dot means its hidden right? So that's one thing I'll have to find through the terminal...

Thanks again.

---

### Post by Bruce M. on 2008-11-28
> **b3n0 said:**
> Thanks once again for your help. I'm going to remove conky and start again following the tools you have given me.
I completely agree, the tut I was following left me clouded and clueless, usually when I follow tuts I actually learn stuff. By the end of the tutorial I had no idea what I had done/changed or what any of the scripting meant.

That's because it wasn't really a tutorial, it was setting up "his" conky on your machine and didn't really explain "why" you need what he said to get.

For example, the fonts he said to download and use. I only use one of those: OpenLogos. And a LOT of people use the PIZZA_DUDE_BULLETS font. I don't.


> **b3n0 said:**
> Is it too much to ask for some help removing it so I can start fresh. As I'm still very fresh with my commands. Also I had a look for that .conkyrc file the dot means its hidden right? So that's one thing I'll have to find through the terminal...

Thanks again.

Whoooooooooaaaaa!
Hope you didn't delete anything, there are two files that you'll need to get again that he mentioned: conky and lm-sensors, plus more if you want a really nice conky showing temperatures.

You don't need the terminal to see/delete hidden files. You can if you want but I'd suggest opening your file manager and under [View] click on the: Show hidden files box.  Much easier that way.

Also since you've downloaded at least two common fonts for conky use you may as well keep them.  If I recall correctly they are in: ~/.fonts (I keep mine there too)

Files I suggest you get:

**conky:** - gee, that one is easy to understand.  :D
> highly configurable system monitor for X based on torsmo
Conky is a system monitor for X originally based on the torsmo code. Since its original conception, Conky has changed a fair bit from its predecessor. Conky can display just about anything, either on your root desktop or in its own window. Conky has many built-in objects, as well as the ability to execute programs and scripts, then display the output from stdout.

**lm-sensors:**
> utilities to read temperature/voltage/fan sensors
Lm-sensors is a hardware health monitoring package for Linux. It allows you to access information from temperature, voltage, and fan speed sensors. It works with most newer systems.

This package contains programs to help you set up and read data from lm-sensors.

I would also suggest:

**curl:**
> Get a file from an HTTP, HTTPS or FTP server curl is a client to get files from servers using any of the supported protocols. The command is designed to work without user interaction or any kind of interactivity.

curl offers a busload of useful tricks like proxy support, user authentication, ftp upload, HTTP post, file transfer resume and more.

and **hddtemp:**
> hard drive temperature monitoring utility
The hddtemp program monitors and reports the temperature of PATA, SATA or SCSI hard drives by reading Self-Monitoring Analysis and Reporting Technology (S.M.A.R.T.) information on drives that support this feature.


As for fonts, it is all a personal choice. But a bit of advice. If "spacing" is one of your priorities (like in my calendar) use a "mono" font. I'm using a mixture of variable width and mono fonts where necessary.

Now saying that, take a look at my [HowTo]("http://ubuntuforums.org/showthread.php?t=867076") in my sig. It doesn't talk about how to "customize" conky, just how to get it installed it to the point that you can customize it for your own personal tastes. It even talks about how to setup multiple conkys.

Hope all this helps.
CHIMO!
Bruce

---

### Post by b3n0 on 2008-11-29
Thanks for your help

I've found the conkyrc file. I've had a play with it and I now have a basic idea of how it works. I'm going to leave it installed. Ill just modify it with Kaivalagi's scripts.

Thanks again.

---

