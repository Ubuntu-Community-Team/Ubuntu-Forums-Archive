---
title: "Asus 900a graphics problem"
date: 2012-06-05
forum: Hardware
---

### Post by Gilgen on 2012-06-05
Hi
Does anyone know how I can resolve this problem on a Asus eeePC 900a running 12.04

**Graphics**  
Adapter Description  - Tungsten Graphics, Inc -- Mesa DRI Intel(R) 945GME x86/MMX/SSE2
Vendor ID -  - Tungsten Graphics, Inc
Device ID - Mesa DRI Intel(R) 945GME x86/MMX/SSE2Driver Version1.4 Mesa 8.0.2
WebGL Renderer - Blocked for your graphics card because of unresolved driver issues.
GPU Accelerated Windows0. -  Blocked for your graphics card because of unresolved driver issues.
AzureBackend - skia

(Treat me gently as I spent too many years playing with windows!!)

Regards
Gilgen

---

### Post by snowpine on 2012-06-05
Welcome to the forums!

What is the problem exactly? What are you trying to do that you get the output above?

Intel 945GME is an extremely low-end graphics chipset, don't expect to be playing hi-def video or graphics-intensive games on your EEE netbook. ;)

---

### Post by Gilgen on 2012-06-05
Hi Snowpine and thanks for the reply. I got the message from Firefox browse "Help" trouble shooter information. I noticed that a lot of graphics were missing on several websites. Couldn't find a solution on Firefox website so I assumed it might be a Ubuntu problem.
Regards
Gilgen

---

### Post by snowpine on 2012-06-05
I do not think lack of GPU accelaration would cause Firefox not to load images? What I would do as a troubleshooting step is to right-click on the image that refuses to load, choose "Copy Link Location," open a new tab, and paste the link into the address bar. Does it load when you do it that way?

If you want to send a link to the site I'd be happy to take a look for you. I actually have an EEE myself with the same graphics card. Or maybe the site is just broken? ;)

---

### Post by Gilgen on 2012-06-05
Hi Snowpine

I found this on the Firefox Help (page down to bottom)

[http://support.mozilla.org/en-US/kb/upgrade-graphics-drivers-use-hardware-acceleration?s=WebGL+Renderer&r=0&e=es&as=s](http://support.mozilla.org/en-US/kb/upgrade-graphics-drivers-use-hardware-acceleration?s=WebGL+Renderer&r=0&e=es&as=s)

The preview won't show all of the link so I've pasted it :-

**I still have problems with my graphics card in Firefox**

 Unfortunately, due to the wide range of possible driver, video card  and operating system combinations, hardware acceleration or 3D web  graphics (WebGL) may still not work for you in Firefox.  In these  instances you fix the problems by disabling hardware acceleration and  WebGL. 
 **Turning off hardware acceleration**

 
[LIST=1]
[*] At the top of the Firefox window, click on the Edit menu and select Preferences
[*] Select the Advanced panel
[*] Select the General tab
[*] Uncheck **Use hardware acceleration where available**.
[*] At the top of the Firefox window, click on the File menu and select Quit.   Start Firefox normally.
[/LIST]
 **Disabling WebGL**

 
[LIST=1]
[*] In the [Location bar]("http://support.mozilla.org/en-US/kb/Location%20bar%20autocomplete"), type **about:config** and press Enter.
[LIST]
[*] The about:config *"This might void your warranty!"* warning page may appear. Click I'll be careful, I promise!, to continue to the about:config page.
[/LIST]
 
[*] In the Filter box, type **webgl.disabled**
[*] Doubleclick on the **webgl.disabled** item to switch it to **true**
[*] At the top of the Firefox window, click on the File menu and select Quit.   Start Firefox normally.
[/LIST]


I tried disabling as they state but still get blanks

This is a an example
[http://order-order.com/](http://order-order.com/)
(I'm a bit of a politics nutter!!)
I have found blanks on other sites as well.

---

### Post by snowpine on 2012-06-05
I don't see any broken images on that site using my Asus EEE 900HA with Intel 945GME graphics.

A couple of suggestions to start troubleshooting would be to view the same page with a different browser (Chrome or Opera for example) and/or view it with another computer on your same network.

---

### Post by Gilgen on 2012-06-06
Hi Snowpine

I checked on my wife's laptop running XP as it has both Firefox and IE installed and all of the links were there with IE but not Firefox. I also installed Midori on the Asus (Ubuntu 12.04) and also get full graphics with it so the problem seems to be exclusively with Firefox and not Ubuntu.

Many thanks for your assistance.

Regards
Gilgen

---

### Post by Gilgen on 2012-06-13
Well I finally resolved the graphics problem .

In Firefox
Help
Troubleshooting Information
Reset Firefox (box in top RH corner)


Job done!

How do I add solved?

---

