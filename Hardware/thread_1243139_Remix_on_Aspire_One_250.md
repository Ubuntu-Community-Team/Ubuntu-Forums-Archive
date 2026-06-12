---
title: "Remix on Aspire One 250"
date: 2009-08-18
forum: Hardware
---

### Post by Fire-Eyes on 2009-08-18
I am looking for fixes...
I have searched and can not find anything that works
problems....

1. No sound ..none  except when I push the test button
2. No Flash...

these are really my problems...

please be patient with me..
I will do my best to keep up.
I am just very upset that this is not working..
8.10 worked on my Toshiba right out of the box
and I could not even get on line via a Ethernet cable..so I am on remix again....now I have these two problems..
I am seriously thinking about putting xp back on and I hate windows..
please someone help me!

---

### Post by Fire-Eyes on 2009-08-18
is there anyone else having these problems?
the only things I can find say they are out dated and the people no longer have the problem, but I do not see the fixes.
Anything would be helpful at this point
thanks

---

### Post by ianmillington on 2009-08-18
Which version of UNR are you running?

---

### Post by Fire-Eyes on 2009-08-18
> **ianmillington said:**
> Which version of UNR are you running?

I am not sure..what is UNR?

---

### Post by ianmillington on 2009-08-18
Ubuntu Netbook Remix

---

### Post by Fire-Eyes on 2009-08-18
> **ianmillington said:**
> Ubuntu Netbook Remix

oh, now I feel silly. I thought there was only one. Jaunty 9.04

---

### Post by ianmillington on 2009-08-18
> **Fire-Eyes said:**
> oh, now I feel silly. I thought there was only one. Jaunty 9.04

Don't be.

There is info about the Acer Aspire one here

[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Acer%20Aspire%20One](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Acer%20Aspire%20One)

Also

[http://ubuntuforums.org/showthread.php?t=1141529](http://ubuntuforums.org/showthread.php?t=1141529)

The sound - I think you need to configure your hardware to use Alsa (analog) rather than Pulse.(see in system settings)

Flash - Do you have it installed?

Have I read you right, you can't get your aspire one onto the internet?

---

### Post by Fire-Eyes on 2009-08-18
I am on the Internet with the remix....

thank you.. I will check out these links
and let you know what I can figure out

I installed the latests flash just last night
can not read any of my on line grocery ads
can not watch HULU
can not watch You Tube
can not play my Flash game (I am way to addicted to it)

---

### Post by ianmillington on 2009-08-18
The Flash one is odd because if I remember correctly with UNR it should work out of the box. Did you install flash from the repositories or the adobe website?

---

### Post by Fire-Eyes on 2009-08-18
> **ianmillington said:**
> The Flash one is odd because if I remember correctly with UNR it should work out of the box. Did you install flash from the repositories or the adobe website?

the web site

---

### Post by ianmillington on 2009-08-18
I suspect that's the problem.

Open a terminal and type 

sudo apt-get install flash

Hit return

Type Your password and hit return

That ought to then download the proper flash installer and then properly install the flash plugin.

Alternatively you can open synaptic package manager and install flashplugin-nonfree

Either of those should fix that for you.

HTH

---

### Post by Fire-Eyes on 2009-08-18
> **ianmillington said:**
> Don't be.

There is info about the Acer Aspire one here

[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Acer%20Aspire%20One](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Acer%20Aspire%20One)

Also

[http://ubuntuforums.org/showthread.php?t=1141529](http://ubuntuforums.org/showthread.php?t=1141529)

The sound - I think you need to configure your hardware to use Alsa (analog) rather than Pulse.(see in system settings)

Flash - Do you have it installed?

Have I read you right, you can't get your aspire one onto the internet?

ok..I read the thread and got completely confused

---

### Post by Fire-Eyes on 2009-08-18
> **ianmillington said:**
> I suspect that's the problem.

Open a terminal and type 

sudo apt-get install flash

Hit return

Type Your password and hit return

That ought to then download the proper flash installer and then properly install the flash plugin.

Alternatively you can open synaptic package manager and install flashplugin-nonfree

Either of those should fix that for you.

HTH

thanks I will try that now!

---

### Post by Fire-Eyes on 2009-08-18
> **ianmillington said:**
> I suspect that's the problem.

Open a terminal and type 

sudo apt-get install flash

Hit return

Type Your password and hit return

That ought to then download the proper flash installer and then properly install the flash plugin.

Alternatively you can open synaptic package manager and install flashplugin-nonfree

Either of those should fix that for you.

HTH

ok I did this

this came up

E: Couldn't find package flash

what should I do now?

---

### Post by ianmillington on 2009-08-18
> **Fire-Eyes said:**
> ok..I read the thread and got completely confused

The reason I took you there was because of your reference to no ethernet. If your ethernet is actually working you can ignore that thread.

---

### Post by ianmillington on 2009-08-18
> **Fire-Eyes said:**
> ok I did this

this came up

E: Couldn't find package flash

what should I do now?

Have you tried the alternative, launching synaptic and searching for the flashplugin-nonfree package?

---

### Post by Fire-Eyes on 2009-08-18
> **ianmillington said:**
> Have you tried the alternative, launching synaptic and searching for the flashplugin-nonfree package?

I have no idea what that means >.<

---

### Post by Fire-Eyes on 2009-08-18
I just ran update manager
and I went to You tube
I got the sound track but the video was choppy then frozen
I am installing GStreamer now...because it said it needed the codex
I hope this helps at least a little..
HULU had a blank screen...

---

### Post by ianmillington on 2009-08-18
In the system section you will find a package manager called synaptic. That contains a list of all the packages available for your system. It will be very rare for you to have to go to a website to install stuff as pretty much everything you are likely to need will be in there.

When you load it you'll be asked for your password. In the left hand pane ensure that "all" is highlighted. In the right hand pane you will see a "search" box. Type "flash" then hit return and everything containing a reference to flash will appear. One of those should be flash plugin. Right click on it and select "mark for installation". then hit apply and your downlaod will begin.

You will also note in the top left hand corner an update button. When you click this your package list will be updated which will mean that you can then upgrade any packages you have installed. There may be quite a few. I would sort out the flash problem first if I were you.

---

### Post by Fire-Eyes on 2009-08-18
> **ianmillington said:**
> In the system section you will find a package manager called synaptic. That contains a list of all the packages available for your system. It will be very rare for you to have to go to a website to install stuff as pretty much everything you are likely to need will be in there.

When you load it you'll be asked for your password. In the left hand pane ensure that "all" is highlighted. In the right hand pane you will see a "search" box. Type "flash" then hit return and everything containing a reference to flash will appear. One of those should be flash plugin. Right click on it and select "mark for installation". then hit apply and your downlaod will begin.

You will also note in the top left hand corner an update button. When you click this your package list will be updated which will mean that you can then upgrade any packages you have installed. There may be quite a few. I would sort out the flash problem first if I were you.

OK..that is done
I never knew about that nook before..thanks
I do not think that solved my problem yet..
is there anything else I can look at?

---

### Post by Fire-Eyes on 2009-08-18
update 
I get sound...That I can barely hear on You Tube
that is it!
I am at my wits end...
why can I not get this to work?
I talked my Mom into Ubuntu 
now she has a new job and can not watch the videos she needs to for work.
I am so screwed!
Thank you so Much for taking the time to help me..
if anyone has any more suggestions please let me know I will try anything at this point.....:confused:

---

### Post by ianmillington on 2009-08-18
Is it just the sound now?

Wonder if it might be a bit easier than you are thinking....

Click on the volume control. Then on the volume control button that appears. There are 2 settings - master (that you control) and PCM (which sets the maximum volume the speakers deliver). Set the PCM to 100% and use the master to set the volume as you like it. That help?

All the best

ian

---

