---
title: "Live Weather Plugin ? Snow? Rain? Wind?"
date: 2008-10-04
forum: General Help
---

### Post by raiderleaf on 2008-10-04
Hi, i am looking to see if any such "live" weather plug in exists that references my zip code and knows the weather, and creates an environment on my desktop to represent it. I live in a polar climate, and it would be cool to see snow on my computer when it is snowing outside, and rain on my computer when it is raining, etc... Possible? anyone have an idea?

Thanks
-raiderleaf

---

### Post by kaivalagi on 2008-10-04
> **raiderleaf said:**
> Hi, i am looking to see if any such "live" weather plug in exists that references my zip code and knows the weather, and creates an environment on my desktop to represent it. I live in a polar climate, and it would be cool to see snow on my computer when it is snowing outside, and rain on my computer when it is raining, etc... Possible? anyone have an idea?

Thanks
-raiderleaf

You could start here: [http://ubuntuforums.org/showthread.php?t=869328](http://ubuntuforums.org/showthread.php?t=869328)
Maybe not quite what you're looking for, but it's a start :)

---

### Post by raiderleaf on 2008-10-04
> **kaivalagi said:**
> You could start here: [http://ubuntuforums.org/showthread.php?t=869328](http://ubuntuforums.org/showthread.php?t=869328)
Maybe not quite what you're looking for, but it's a start :)

Do you have any pictures of this in action? I don't know if that is exactly what I'm after, but the description is a little unclear to me, and if you would clarify it with words or a few images that would be great!

Thanks
-raiderleaf

---

### Post by hansdown on 2008-10-04
Hi kaivalagi.

If you right click on your top menu bar, then select add to panel, you should get a list of things you can add. Weather report is one, I think.

You will need to set it to your area in preferances.

---

### Post by raiderleaf on 2008-10-04
> **hansdown said:**
> Hi kaivalagi.

If you right click on your top menu bar, then select add to panel, you should get a list of things you can add. Weather report is one, I think.

See the weather plug in is easy, there are so many that just tell temperature and such, but I want one that SHOWS it on the screen. If its 15 degrees and snowing, I would like to see snow blowing on my screen and such, and when its 65 and raining i'd love to see rain... I hope its possible....

Thanks
-raiderleaf

---

### Post by kaivalagi on 2008-10-04
My conkyForecast script can display a font on the desktop which depicts the weather...but if you want something that animates the weather on your desktop, I haven't seen such a thing....yet

---

### Post by kaivalagi on 2008-10-04
> **hansdown said:**
> Hi kaivalagi.

If you right click on your top menu bar, then select add to panel, you should get a list of things you can add. Weather report is one, I think.

You will need to set it to your area in preferances.

Tell me something I don't know :)

The script I've created might help kick off an effect...but the effect will need to be created by someone else...

---

### Post by raiderleaf on 2008-10-04
> **kaivalagi said:**
> My conkyForecast script can display a font on the desktop which depicts the weather...but if you want something that animates the weather on your desktop, I haven't seen such a thing....yet

When you say a 'Font' that depicts the weather, I don't quite understand what you mean... screenshot?

---

### Post by kaivalagi on 2008-10-04
> **raiderleaf said:**
> When you say a 'Font' that depicts the weather, I don't quite understand what you mean... screenshot?

[http://ubuntuforums.org/attachment.php?attachmentid=80833&d=1218292902](http://ubuntuforums.org/attachment.php?attachmentid=80833&d=1218292902)

My current weather output attached

The script is used in conjunction with Conky, a tool used to output text info straight onto the desktop: [http://conky.sourceforge.net]("http://conky.sourceforge.net")

---

### Post by raiderleaf on 2008-10-04
Yeah thats not what I'm after really... any ideas where I could look?

---

### Post by kaivalagi on 2008-10-04
> **raiderleaf said:**
> Yeah thats not what I'm after really... any ideas where I could look?

There is something that can change your desktop wallpaper called "weather-wallpaper", you can find it here: [http://mundogeek.net/weather-wallpaper/](http://mundogeek.net/weather-wallpaper/)

Other than that, I think there isn't anything available for what you want...

---

### Post by raiderleaf on 2008-10-05
Well, that is okay for right now... any software that can make it "snow" on my screen though that is UBUNTU 8.04 stable?

---

### Post by cammin on 2008-10-05
I got this from the compiz forums
```
dbus-send --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/snow/allscreens/toggle_key org.freedesktop.compiz.activate string:'root' int32:`xwininfo -root | grep id: | awk '{ print $4 }'`
```

It is the code to get compiz to start snowing.

So find something that checks the weather and can run a that code when the weather is snow.

---

### Post by kaivalagi on 2008-10-05
> **cammin said:**
> I got this from the compiz forums
```
dbus-send --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/snow/allscreens/toggle_key org.freedesktop.compiz.activate string:'root' int32:`xwininfo -root | grep id: | awk '{ print $4 }'`
```

It is the code to get compiz to start snowing.

So find something that checks the weather and can run a that code when the weather is snow.

In conjunction with the above and my script, the desired effect could be achieved

My script outputs the following characters for use with the ConkyWeather font:

```
conditions_weather_font = {
        "0": u"1", #Tornado
        "1": u"2", #Tropical Storm
        "2": u"3", #Hurricane
        "3": u"n", #Severe Thunderstorms
        "4": u"m", #Thunderstorms
        "5": u"x", #Mixed Rain and Snow
        "6": u"x", #Mixed Rain and Sleet
        "7": u"y", #Mixed Precipitation
        "8": u"s", #Freezing Drizzle
        "9": u"h", #Drizzle
        "10": u"t", #Freezing Rain
        "11": u"h", #Light Rain
        "12": u"i", #Rain
        "13": u"p", #Snow Flurries
        "14": u"p", #Light Snow Showers
        "15": u"8", #Drifting Snow
        "16": u"q", #Snow
        "17": u"u", #Hail
        "18": u"w", #Sleet
        "19": u"7", #Dust
        "20": u"0", #Fog
        "21": u"9", #Haze
        "22": u"4", #Smoke
        "23": u"6", #Blustery 
        "24": u"6", #Windy
        "25": u"-", #N/A
        "26": u"f", #Cloudy
        "27": u"D", #Mostly Cloudy - night
        "28": u"d", #Mostly Cloudy - day
        "29": u"C", #Partly Cloudy - night
        "30": u"c", #Partly Cloudy - day
        "31": u"A", #Clear - night
        "32": u"a", #Clear - day
        "33": u"B", #Fair - night
        "34": u"b", #Fair - day
        "35": u"v", #Mixed Rain and Hail
        "36": u"5", #Hot
        "37": u"k", #Isolated Thunderstorms - day
        "38": u"k", #Scattered Thunderstorms - day
        "39": u"g", #Scattered Showers - day
        "40": u"j", #Heavy Rain
        "41": u"o", #Scattered Snow Showers - day
        "42": u"r", #Heavy Snow
        "43": u"r", #Heavy Snow
        "44": u"-", #N/A
        "45": u"G", #Scattered Showers - night
        "46": u"O", #Scattered Snow Showers - night
        "47": u"K", #Isolated Thunderstorms - night
        "na": u"-", #N/A
        "-": u"-" #N/A
    }
```

It would be run as follows to get one of those letters to be output:

```
conkyForecast --location=UKXX0103 --datatype=WF
```

You'd just need to wrap that call with a shell script, and when the letters output relate to snow (i.e. for a "p", "8" and "q"), call the dbus command above...

I'll leave you with that idea....have a play and see what you can achieve...

---

### Post by raiderleaf on 2008-10-05
> **kaivalagi said:**
> In conjunction with the above and my script, the desired effect could be achieved

You'd just need to wrap that call with a shell script, and when the letters output relate to snow (i.e. for a "p", "8" and "q"), call the dbus command above...

I'll leave you with that idea....have a play and see what you can achieve...

So first I have to uninstall the weather wallpaper, then I have to install this conky weather plugin, then I do what the guy said above that with the snow effect, but what are you talking about with regards to the "shell script"? I don't even know what a shell script is, and I'm fairly new to programming in linux. How do I go about this, and how can I get it so that it automatically updates?

Thanks,
raiderleaf

---

### Post by kaivalagi on 2008-10-05
> **raiderleaf said:**
> So first I have to uninstall the weather wallpaper, then I have to install this conky weather plugin, then I do what the guy said above that with the snow effect, but what are you talking about with regards to the "shell script"? I don't even know what a shell script is, and I'm fairly new to programming in linux. How do I go about this, and how can I get it so that it automatically updates?

Thanks,
raiderleaf

If you create a shell script (loads of help online for that) to call the "dbus..." command when you receive the right output from conkyForecast, you should be set. The shell script could be run using cron, say every 15 minutes....type "man crontab" for info on cron

I'd suggest the first thing to do is to make sure compiz can do what you need it to, and can toggle the effect with that "dbus..." command.

I would help further but I no interest in having compiz put snow on my desktop...

---

### Post by raiderleaf on 2008-10-05
> **kaivalagi said:**
> If you create a shell script (loads of help online for that) to call the "dbus..." command when you receive the right output from conkyForecast, you should be set. The shell script could be run using cron, say every 15 minutes....type "man crontab" for info on cron

I'd suggest the first thing to do is to make sure compiz can do what you need it to, and can toggle the effect with that "dbus..." command.

I would help further but I no interest in having compiz put snow on my desktop...

Sorry, I really don't understand what you mean. The whole shell script thing, I don't know what it does, how to do it, where to find it, etc, and how to syncronize that with the conkyForecast thing just boggles my mind... if you have time, i'd love some insight on it. Thanks :-D

---

### Post by linkmaster03 on 2008-10-05
First, you should know what a shell is. A shell can be related to the command prompt on Windows. It's the text interface to managing your system. 'bash' is by far the most popular shell on a Linux distribution, like Ubuntu. So, a shell script, which is the same thing is a bash script (in most cases), is a file of text that is fed to the shell, and the commands are sent to the shell. It can be a file you can run to execute many commands easily because you only have to execute that one file. Shell scripting also contains what a normal programming language will, like if-then conditionals, for loops, etc.

I don't know if that is understandable, but I hope it helps you. :)

---

### Post by raiderleaf on 2008-10-05
> **linkmaster03 said:**
> First, you should know what a shell is. A shell can be related to the command prompt on Windows. It's the text interface to managing your system. 'bash' is by far the most popular shell on a Linux distribution, like Ubuntu. So, a shell script, which is the same thing is a bash script (in most cases), is a file of text that is fed to the shell, and the commands are sent to the shell. It can be a file you can run to execute many commands easily because you only have to execute that one file. Shell scripting also contains what a normal programming language will, like if-then conditionals, for loops, etc.

I don't know if that is understandable, but I hope it helps you. :)

Yeah, unfortunately that doesn't help me that much. I am just getting into linux and this all is rocket science to me sadly.... is there anyway someone can walk me through it or try to do it themselves and let me know how or how it worked out?

---

### Post by kaivalagi on 2008-10-06
Okay, before you even attempt to write a "shell script", I think we need to establish whether or not you can get the compiz effect you want working on your desktop...if that doesn't work then there is no point going any further...

Once that is up and running, search google and read about shell scripts, it's not too difficult, start here maybe: [http://en.wikipedia.org/wiki/Bourne_shell](http://en.wikipedia.org/wiki/Bourne_shell))

---

### Post by raiderleaf on 2008-10-06
> **cammin said:**
> I got this from the compiz forums
```
dbus-send --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/snow/allscreens/toggle_key org.freedesktop.compiz.activate string:'root' int32:`xwininfo -root | grep id: | awk '{ print $4 }'`
```

It is the code to get compiz to start snowing.

So find something that checks the weather and can run a that code when the weather is snow.

So how do I test this code? I tried just putting it in the terminal but that did nothing, it just went to the next line of prompt...

---

### Post by cammin on 2008-10-07
Can you enable snow through Compiz settings manager?
I don't use Compiz so I can't confirm that the dbus message works.

While researching this issue, I found this:


[http://forum.compiz-fusion.org/showthread.php?t=7418](http://forum.compiz-fusion.org/showthread.php?t=7418)

Someone did all the work for you.

---

### Post by raiderleaf on 2008-10-08
> **cammin said:**
> Can you enable snow through Compiz settings manager?
I don't use Compiz so I can't confirm that the dbus message works.

While researching this issue, I found this:


[http://forum.compiz-fusion.org/showthread.php?t=7418](http://forum.compiz-fusion.org/showthread.php?t=7418)

Someone did all the work for you.


THAT LOOKS GREAT!!! The only thing is that I still have no clue how to compile that code, and in the rest of the body they mention something about the Compiz front end??? Some help with this would be greatly appreciated.

---

### Post by kaivalagi on 2008-10-08
> **raiderleaf said:**
> THAT LOOKS GREAT!!! The only thing is that I still have no clue how to compile that code, and in the rest of the body they mention something about the Compiz front end??? Some help with this would be greatly appreciated.

You need to do some reading, search the forums for detail on compiz.

I found a couple threads that might help you.

How-to: Getting the funky Compiz Screensaver in Hardy
[http://ubuntuforums.org/showthread.php?t=889317](http://ubuntuforums.org/showthread.php?t=889317)

The Great Desktop Effects FAQ of 2008
[http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695)

---

### Post by raiderleaf on 2008-10-08
> **kaivalagi said:**
> You need to do some reading, search the forums for detail on compiz.

I found a couple threads that might help you.

How-to: Getting the funky Compiz Screensaver in Hardy
[http://ubuntuforums.org/showthread.php?t=889317](http://ubuntuforums.org/showthread.php?t=889317)

The Great Desktop Effects FAQ of 2008
[http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695)

I don't understand exactly how to add those repositories to the synaptic as mentioned in the first link. I don't know how any of this is going to work to start. Does it help that I have the Emerald Theme Manager installed which has given me a Compiz icon???

---

### Post by kaivalagi on 2008-10-09
> **raiderleaf said:**
> I don't understand exactly how to add those repositories to the synaptic as mentioned in the first link. I don't know how any of this is going to work to start. Does it help that I have the Emerald Theme Manager installed which has given me a Compiz icon???

open Administration->Synaptic Package Manager
goto menu Settings->Repositories
select the third party software tab and click add
enter the url for the repo from the linked thread I gave you
then on the main menu bar select "Reload"

You'll then be able to search for the new apps available deom the repo, select and install them

Hope that helps

Any questions about the what's in the howto threads I linked should be asked there, where people have been through the process, I haven't so my usefulness stops here :)

---

### Post by raiderleaf on 2008-10-10
> **kaivalagi said:**
> open Administration->Synaptic Package Manager
goto menu Settings->Repositories
select the third party software tab and click add
enter the url for the repo from the linked thread I gave you
then on the main menu bar select "Reload"

You'll then be able to search for the new apps available deom the repo, select and install them

Hope that helps

Any questions about the what's in the howto threads I linked should be asked there, where people have been through the process, I haven't so my usefulness stops here :)

I made a post on that forum, please read it. I don't know why it isn't working in the installation process. it is the first link that you quoted, or just go here
[http://ubuntuforums.org/showthread.php?t=889317](http://ubuntuforums.org/showthread.php?t=889317)

---

