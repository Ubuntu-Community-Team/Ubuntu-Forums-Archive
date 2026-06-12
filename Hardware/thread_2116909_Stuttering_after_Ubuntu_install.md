---
title: "Stuttering after Ubuntu install"
date: 2013-02-17
forum: Hardware
---

### Post by Zirts on 2013-02-17
Hi,

So I'm experiencing some stuttering like every 7 minutes. Gnome-system-monitor shows that CPU  core 1 goes to 100% capacity while CPU core 2 stays put when stuttering happens. Is this just a sign I should soon think about a new laptop or might it be a faulty installation of my OS?

---

### Post by sudodus on 2013-02-17
I think you should check a few things before giving up your computer.

You can start by checking with ```
top
``` which program is keeping your computer busy at those instances.

It could be a problem with too much swappiness. See this link

[[COLOR="Red"]https://help.ubuntu.com/community/SwapFaq[/COLOR]]("https://help.ubuntu.com/community/SwapFaq")

> The default setting in Ubuntu is swappiness=60. Reducing the default value of swappiness will probably improve overall performance for a typical Ubuntu desktop installation. A value of swappiness=10 is recommended, but feel free to experiment. Note: Ubuntu server installations have different performance requirements to desktop systems, and the default value of 60 is likely more suitable.

---

### Post by Zirts on 2013-02-17
Allright..  So my swappiness is 10 which is ok but it seems that Xorg takes about 50% CPU when that stutter occurs...   Have any idea how to troubleshoot further from there?

---

### Post by sudodus on 2013-02-17
> **Zirts said:**
> Allright..  So my swappiness is 10 which is ok but it seems that Xorg takes about 50% CPU when that stutter occurs...   Have any idea how to troubleshoot further from there?

Yes, swappiness 10 should be OK

I guess it means 100% of one core. Can you see if swapping occurs or if there is some other writing to or from the disk?
top should show if 'swap used' increases. To get more info about read/write, you can install iotop and run
```
sudo iotop -o
```

- What are the computer specs: cpu, ram, graphics chip/card?
- What graphics driver are you running?

---

### Post by Zirts on 2013-02-17
Computer specs:
AMD Athlon(tm) II P340 Dual-Core Processor × 2  rated at 2.20 GHz
4 GB RAM
Mobility Radeon HD 5650

I'm using the latest AMD non-beta propietary drivers (13.1)

And the iotop -o has the information coming and going from the screen so fast that I fail to see what happened really as I have to first see when stuttering occurs, then see that it is xorg causing it and then see on the other window what happened in iotop :D  Is there a way to log it to txt file maybe?

---

### Post by sudodus on 2013-02-17
You can change the delay with the -d option

```
iotop -od 5
```
means refreshing every 5 seconds instead of every second. See ```
man iotop
``` for more details

---

### Post by sudodus on 2013-02-17
How is your graphics with the built-in driver (instead of the proprietary one)? I guess you have tried that.

---

### Post by Zirts on 2013-02-17
Allright. I did not see anything in iotop when Xorg went up in the CPU column of top. But then again iotop was using 100% of my CPU so maybe it was just a minor increase from xorg not the real stutter. Was a bit hard to see heh.

I installed this OS about 1.5 month ago, and installed the propietary driver right after that. As I remember the 3D performance was pretty bad for my card with the Gallium driver so I just downloaded the proprietary one.

---

### Post by mörgæs on 2013-02-17
As mentioned above, please try **top**. Best is to keep it running for some time while doing normal work. 

Which application is high in %CPU?

---

### Post by sudodus on 2013-02-17
> **Zirts said:**
> Allright. I did not see anything in iotop when Xorg went up in the CPU column of top. But then again iotop was using 100% of my CPU so maybe it was just a minor increase from xorg not the real stutter. Was a bit hard to see heh.

I installed this OS about 1.5 month ago, and installed the propietary driver right after that. As I remember the 3D performance was pretty bad for my card with the Gallium driver so I just downloaded the proprietary one.
I am very surprised that ***iotop*** should use 100% of your cpu. What happens when you shut it off again? (I guess you use two terminal windows, one with top and one with iotop.)

---

### Post by sudodus on 2013-02-17
Could there be some problem with reading/writing, that sometimes keeps the computer busy re-reading or re-writing?

Have you checked the S.M.A.R.T. status of your HDD?

---

### Post by Zirts on 2013-02-17
S.M.A.R.T shows that everything is OK but I have to say that I can hear that little noise from my HDD allready which should be a sign that soon the screetching sound will come and I need a new HDD. 

But now to the iotop and top tests. 
So I watched a video and at the same time I had two terminals open one with top and one with iotop -o -d7 

iotop showed me that gnome-shell was disk reading with 100 KB/s if i remember correctly now ( was the biggest one there) when the stutter occurred and Xorg took 60% cpu usage.  I will wait up one more stutter and take a screenshot this time which I should have done long ago.

Edit: uploaded pictures. iotop did not update at the exact same time when Xorg went up but the picture after shows it's aftermath.

---

### Post by sudodus on 2013-02-17
> **Zirts said:**
> S.M.A.R.T shows that everything is OK but I have to say that I can hear that little noise from my HDD allready which should be a sign that soon the screetching sound will come and I need a new HDD. 

No I don't think it is the HDD.
> 
But now to the iotop and top tests. 
So I watched a video and at the same time I had two terminals open one with top and one with iotop -o -d7 

iotop showed me that gnome-shell was disk reading with 100 KB/s if i remember correctly now ( was the biggest one there) when the stutter occurred and Xorg took 60% cpu usage.  I will wait up one more stutter and take a screenshot this time which I should have done long ago.

Edit: uploaded pictures. iotop did not update at the exact same time when Xorg went up but the picture after shows it's aftermath.
I think we can use your screenshots to understand what is happening. And I hope some other guys might add ideas too :-P

As far as I can see, xorg is not causing any swapping, and it should not be responsible for reading from the video file. I think that it cannot quite keep the pace necessary to show the video smoothly.

I cannot see any information about the version and flavour of Ubuntu except [ubuntu] in the title.

- Is it 12.04 LTS or 12.10?
- What desktop environment is it? Unity or some other flavour of gnome 3 shell? Are you running compiz?

I suggest that you try

- either to download iso files of Lubuntu and Xubuntu and try them live (testing with VLC (temporary install into the live session). Maybe this is more complicated, but it does not mess with your installed system

- or install the corresponding desktop environments into your present Ubuntu. This is easy to do, and should not destroy anything, but your menus might become a bit cluttered.

```
sudo apt-get install lubuntu-desktop
sudo apt-get install xubuntu-desktop

```

And you can select desktop environment at the log in screen.

My experience is that Lubuntu plays video much better than [vanilla] Ubuntu, because the its desktop environment LXDE is ultra light-weight.

You get extreme speed if you have no desktop environment at all, only the openbox window manager, that you can also select at the log in screen (if you have Lubuntu or lubuntu-desktop). Right-click on the background to get a terminal window and go ahead ...

I guess you think that you should get both eye-candy and speed, but maybe you can select different desktop environments depending on the task.

---

### Post by Zirts on 2013-02-17
It's a 12.10 Ubuntu with gnome 3 desktop manager. I just like the looks of this DM. But I will give your advice a try then. Can post results later tough as my internet download speed is slow and I will need time to fetch the new DM.

---

### Post by Zirts on 2013-11-16
Fixed it. Just re-installed the OS, was like chasing a ghost when trying to fix it without a complete re-install.

---

