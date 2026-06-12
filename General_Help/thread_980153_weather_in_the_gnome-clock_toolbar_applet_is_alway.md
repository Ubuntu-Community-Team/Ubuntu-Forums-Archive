---
title: "weather in the gnome-clock toolbar applet is always wrong"
date: 2008-11-12
forum: General Help
---

### Post by ricardisimo on 2008-11-12
Or is it just Pasadena, CA? It's regularly reading temperatures like 40° F or even below 0°. Trust me, the day it falls below zero Fahrenheit in Pasadena, you will be reading about it in your local newspapers.

Is there anything that can be done about this?

---

### Post by ricardisimo on 2008-11-13
Does anyone else even use the weather applet? Does it work in your city?

---

### Post by LowSky on 2008-11-13
mine works fine, I would check to make sure you got the right zip code or city, maybe use another town that is local to you.

I believe the application gets it data from Weather.com

---

### Post by ricardisimo on 2008-11-13
No, we're the only "Pasadena" in California, and Weather.com has the correct info, as does every other website I can find. Or they are within 5° of reality, at least. I can look out the window and see what my own weather is like; that's not really the point. I'm more concerned that the info is wildly off for everyone.

---

### Post by bapoumba on 2008-11-13
Is this the correct location ? I could not find Pasadena in the applet list, so I choose Burbank, which looks close on the map. Is the weather correct ?

---

### Post by dlmoak on 2008-11-13
Works fine for Jackson, MS.  USA  Ubuntu 8.10 64-bit

---

### Post by ricardisimo on 2008-11-13
> **bapoumba said:**
> Is this the correct location ? I could not find Pasadena in the applet list, so I choose Burbank, which looks close on the map. Is the weather correct ?

Yup, that's Pasadena right next to Burbank, and the weather looks just right. Interestingly, so does Pasadena's... my applet says 81°, which is just about dead-on, for the first time since I installed Ibex two weeks ago. I wonder if one of the maintainers read my post. :-)

---

### Post by jimv on 2008-11-13
Mine has been doing the same thing, and I just changed the city, then changed it back and it seems to be fine now.

---

### Post by ricardisimo on 2008-11-14
That lasted all of about a day. It's off by 15° at least. Is this a bug I should report, or just faulty info coming from somewhere down the line?

---

### Post by bapoumba on 2008-11-15
I do not know. The weather applet has always been working for me..

---

### Post by ricardisimo on 2008-11-16
Damn it's cold!! Oh my god!... Right now the gnome-clock says it's -99° out here in Pasadena! These must be the end times! Farewell everyone!

Just on the off chance that the Rapture is ***not*** upon us, I'll go ahead and file a bug report with whomever it is the developers use for such things.

---

### Post by bapoumba on 2008-11-16
> **ricardisimo said:**
> Damn it's cold!! Oh my god!... Right now the gnome-clock says it's -99° out here in Pasadena! These must be the end times! Farewell everyone!

Just on the off chance that the Rapture is ***not*** upon us, I'll go ahead and file a bug report with whomever it is the developers use for such things.
I've searched bug reports, but could not find anything describing exactly your situation (please forgive me, but I think it is a funny one, -99° that's hilarious ;))

As I could not find Pasadena from the applet menu, please try with Burbank and see if it works. If there is no weather station in Pasadena, that might explain it.

2 bug reports with some info that may help you track down your issue:
[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/216197](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/216197)
[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/232375](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/232375)

---

### Post by oldsoundguy on 2008-11-16
Did you know???? LOL you can place more than ONE weather applet in the panel?  Yep, and monitor more than one city!!  Just don't put TOOOOOOO many, or the confusion may be too much ... lol
You can also keep the confusion down if you put one applet in the bottom and one in the top panels!

---

### Post by ricardisimo on 2008-11-16
Viewing incorrect weather reports in multiple cities is indeed tempting, but I went and filed a [bug report]("http://bugzilla.gnome.org/show_bug.cgi?id=561017") on this issue all the same.

I doubt this is an actual bug... more like someone typed in the wrong ZIP code somewhere along the line, but whatever. Someone out there might actually need to know the correct weather in Pasadena one day, during the Rose Parade or something. We can't have a Tournament of Roses if it's 99" below zero. Heavens no.

I like imagining that whoever handles the Pasadena thermometer is just trying to screw with everyone... they put it in the oven one day, freezer the next, then in their dog's rectum just for a hoot. LOL. I slay me.

---

### Post by oldsoundguy on 2008-11-16
Since Ubuntu has absolutely NO control over the data being submitted by the NWS/Weather Channel, seriously doubt that the issue is the applet and much more likely a glitch in the NWS/Weather Channel reporting for occupied Pasadena. All that applet does in CONNECT you to the service. (it phones home for the information.)
Think about the applet this way .. it is just a URL to a web page and it displays what is ON that web page.
(try another town nearby and see if there is a problem .. also make sure your PREFERENCES are the way you want them including the report check intervals)
I monitor my local airport and also my old stomping grounds.  Nary an issue and never has been for well over a year on 4 machines.

---

### Post by digbigbrotherjenson on 2009-01-03
I'm in Western Europe (Brussels) and my gnome weather display is also very wrong. It's freezing at the moment and there is occasional snow and bad weather while the gnome weather monitor reports shiny warm weather like in the summertime while it's winter here ...

One should file a bug report please so we can get this fixed ...
For now i'm simply removing the weather information untill it's fixed.

---

### Post by oldsoundguy on 2009-01-03
once again, the weather applet leads to what can be called a WEB PAGE.  It reads and relays what is on that page back to your computer and displays what it finds.  If the information at the source is wrong, that is not the fault of the applet!

The old axiom GIGO applies in full.  The developers of Ubuntu and of those applets have no control over what is input at the other end.  It is just reading a misprint in a book and showing it to you.

BUT .. make sure you have your preferences set up properly as to the units of measure you wish to be displayed. (right click .. preferences).

---

### Post by kaivalagi on 2009-01-03
In case this helps, the following URL can be used to see the location codes for use with the gnome weather applet.

[http://svn.gnome.org/viewvc/libgweather/trunk/data/Locations.xml.in?view=markup](http://svn.gnome.org/viewvc/libgweather/trunk/data/Locations.xml.in?view=markup)
 
Just a thought, hope it helps

---

### Post by ricardisimo on 2009-01-03
> **oldsoundguy said:**
> once again, the weather applet leads to what can be called a WEB PAGE.  It reads and relays what is on that page back to your computer and displays what it finds.  If the information at the source is wrong, that is not the fault of the applet!

The old axiom GIGO applies in full.  The developers of Ubuntu and of those applets have no control over what is input at the other end.  It is just reading a misprint in a book and showing it to you.

BUT .. make sure you have your preferences set up properly as to the units of measure you wish to be displayed. (right click .. preferences).

I understand what you're saying, but then it's not as though the people at Firefox have set up their own weather station in Pasadena. Yet, the ForecastFox toolbar is normally right on the money. How's that possible? It's possible because they have chosen a service which works well, while Gnome hasn't. At least, that's one way of looking at it. They could change at any moment, I'd say.

---

### Post by kaivalagi on 2009-01-03
If you use conky then why not try my weather forecast script (see my sig) which uses weather.com, alternatively if you use AWN then try the weather applet for that which uses weather.com...both work fine for me and are always visible.

Weather.com uses location codes (e.g. UKXX0103) not like those in the panel applet and clock, which leads me to believe either the panel applet doesn't use weather.com or does but interprets gui settings to codes and maybe gets it wrong.

In any case all you can do is raise the issue, currently for Pasadena, California it says it's -73C (feels like -87.7C)...

---

