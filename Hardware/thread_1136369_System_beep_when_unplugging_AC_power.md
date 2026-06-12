---
title: "System beep when unplugging AC power"
date: 2009-04-24
forum: Hardware
---

### Post by 3dmaker on 2009-04-24
Hello, I just recently switched to Ubuntu on my new lenovo 3000 G530. I have been using linux for multiple years, but I have a problem with this computer. Whenever I unplug the AC power cable, the system makes a beep that is about 200% louder than it should be. I have tried disabling pcspkr, but that doesn't work. Whenever I mute my sound, the computer does not beep. 
In Vista (the OS that came with this computer, all I had to do was disable system beep).
Currently, if I go to System>Preferences>Sound, there is no System Bell tab. 
If anyone has any ideas on what to do, please let me know ASAP.

---

### Post by drubin on 2009-05-08
Hi

I currently also am having this issue.  Lenvo 3000 N500 laptop, I have fond a temp soution is to just mute the laptop when plugging in and out the power fn+esc or pressing the touch sensors in the top right hand corner.

The think pads claim to have a bios setting but wee don't seem to.

btw I have also tried removing the kernel module setting it in gconf sound and prefs and still the only thing that seems to work is the mute button.

Not cool but I hope they release a bio setting because I often forget to press it and it annoys the whole household.

---

### Post by StuartN on 2009-05-08
> **3dmaker said:**
> If anyone has any ideas on what to do, please let me know ASAP.

In System->Preferences->Sound, click on the "Sounds" tab and uncheck "Play alert sound".

---

### Post by drubin on 2009-05-08
> **StuartN said:**
> In System->Preferences->Sound, click on the "Sounds" tab and uncheck "Play alert sound".

That was the first thing I tried. for now the only solution is to use the mute sensor key that mutes all sound while plugging in the power

---

### Post by swisstone198 on 2009-05-08
have you run 

#modprode -r pcspkr

??

---

### Post by shoby on 2009-05-08
Friends!!

please see the following link may this will help you with your issues. 

[http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-4CSRG4](http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-4CSRG4)


thanks,

---

### Post by drubin on 2009-05-08
> **swisstone198 said:**
> have you run 

#modprode -r pcspkr

??
I have :) (2nd thing I tried)

> **shoby said:**
> Friends!!

please see the following link may this will help you with your issues. 

[http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-4CSRG4](http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-4CSRG4)


thanks,

Sorry but how does palm OS help with lenvo running Ubuntu Linux?
{title}FAQ about Palm OS 3.3 upgrade - IBM WorkPad {/title}

---

### Post by diggiewiggie on 2009-06-03
I have the same problem on my ideapad s10...
this is pretty annoying when i plug in earphone and suddenly the electricity fails, it feels like the beep breaking my ears...
this is a serious problem for me, i suppose, since i might do damage to my hearing...

I do hope someone could come up with a solution.

thanks.

---

### Post by Lancen833 on 2009-07-06
Has anyone found a fix for this yet? 
It's extraordinarily annoying when I'm not wearing headphones, but when I am the noise is deafening. 
It has put me off of headphones of any kind on my laptop. :(

---

### Post by levi-civita on 2009-09-11
I have the same problem on jaunty. When i plug off the AC cable system beeps every 2 seconds. It started suddenly when the charge was empty and ubuntu turned off the computer. Casper m54se model machine. Any solution ?

---

### Post by dawian on 2009-11-22
modprobe -r pcspkr command works. there is no more beep after running it.

---

### Post by oppression on 2010-04-27
This command does not stop the beep modprobe -r pcspkr !!!
Has found somebody the solution for this problem?

---

### Post by dougamos on 2011-02-28
I don't believe you can change this from Ubuntu.  I had the exact same problem and was able to disable the beep/alarm by changing some bios settings.

For my laptop (Thinkpad R61) it was under Config->Alarms

---

### Post by Yellow Pasque on 2011-02-28
Make sure snd_pcsp module is not loaded. Also, check alsamixer to see if you have a separate beep volume (my HP dv6-3120 does).

---

### Post by brakos on 2011-03-31
> **Temüjin said:**
> Make sure snd_pcsp module is not loaded. **Also, check alsamixer to see if you have a separate beep volume (my HP dv6-3120 does).**

Didn't turn it off on my Lenovo G530 24G, but it did make it a lot less deafening. And with my wonky power cord, that's a very good thing :)

---

