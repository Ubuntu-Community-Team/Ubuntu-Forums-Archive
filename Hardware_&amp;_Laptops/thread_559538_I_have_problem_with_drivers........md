---
title: "I have problem with drivers......."
date: 2007-09-25
forum: Hardware &amp; Laptops
---

### Post by walla90 on 2007-09-25
[SIZE=4][COLOR=Black]**Hello! I am new with Linux....**.

I have a laptop model: MSI Megabook S260
witch included this graphic card: Intel 915 GM
I have download the driver from Intel site:  
“i915Graphics.tar.gz“
I want to know how to install this driver....

Help!!!!!!!!!!!!!!


Thank you guys very match....[/COLOR]   
[/SIZE]

---

### Post by pay on 2007-09-25
What version of Ubuntu are you using? That driver should already be installed. Are you having problems with you display?

---

### Post by walla90 on 2007-09-25
[SIZE=4][COLOR=Black]My Ubuntu software version is 7.04[/COLOR][/SIZE]
 [SIZE=4][COLOR=Black]I have no problems with my display.[/COLOR][/SIZE]
 [SIZE=4][/SIZE] 
 [SIZE=4][COLOR=Black]My resolution is to small 1024X768[/COLOR][/SIZE]
 [SIZE=4][COLOR=Black]And I want to rise it up.[/COLOR][/SIZE]
 [SIZE=4][COLOR=Black]I search the internet, and some people said to install the driver.[/COLOR][/SIZE]
 [SIZE=4][/SIZE] 
 [SIZE=4][COLOR=Black]thanks......[/COLOR][/SIZE]

---

### Post by pay on 2007-09-25
I think I was wrong with it being installed by default (stupid ati user). Try ```
sudo aptitude install 915resolution
```

---

### Post by walla90 on 2007-09-25
[B]After i run this commend nothing change!!!!

please HELP ME[/B]

---

### Post by pay on 2007-09-26
** How to Correct the Graphics Resolution (Intel) **

 [LIST]
[*]Read [#How to enable Large Widescreen Support]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_enable_Large_Widescreen_Support") if you have a larger (>20") monitor[/LIST] [LIST]
[*]Intel 915g, 945g, etc. graphics chipsets only have a limited set of resolutions initially installed, despite the correct driver being detected.
[*]Install the resolution altering tool:[/LIST] sudo apt-get install 915resolution
[LIST]
[*]Run the following to see the availible modes:[/LIST] 915resolution -l
[LIST]
[*]Choose a resolution you don't need and replace, for example the following changes 1920x1440 to 1920x1200[/LIST] 915resolution 5c 1920 1200
[LIST]
[*]This should add the option for that resolution to the "System>Preferences>Screen Resolution" tool.
[*]If it works correctly then you can make the change permanent:[/LIST] sudo gedit /etc/rc.local
[LIST]
[*]Simply add the command you typed in above before:[/LIST] exit 0

---

### Post by walla90 on 2007-09-26
It's not working:
"
Intel 800/900 Series VBIOS Hack : version 0.5.2

Unable to obtain the proper IO permissions: Operation not permitted
"

what to do?

---

