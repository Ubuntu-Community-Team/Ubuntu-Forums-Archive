---
title: "Dispaly Resolution"
date: 2006-07-10
forum: Hardware &amp; Laptops
---

### Post by gzilla on 2006-07-10
Hello Y'all,

I've just installed ubuntu 6.06 my Dell inspiron 1100 laptop. The problem is that the display resolution defaults to [COLOR="Red"]**640x480**[/COLOR]. There is no choice of selecting the proper display resolution of 1028x786. I've re-intalled several times hoping for a selection of display  settings to select the right one but all I get is one - 640x480.

Please, how can I fixed this or get round it? Its impossible using this current display setting to anything.

Tanx

Gzilla

---

### Post by florizs on 2006-07-10
The trick with this is to configure the X-server. 
I suppose you are a beginner?

This post on the forums concerns your problem,
[http://www.ubuntuforums.org/showthread.php?t=190022]("http://www.ubuntuforums.org/showthread.php?t=190022")
If you have any troubles you should reply to that post.

Good Luck!

---

### Post by strabes on 2006-07-10
I have the dell inspiron e1705 with radeon x1400 and I am trying to get my resolution above 1440x900. on a fresh install the max resolution was much lower than that, but I install the linux radeon driver and now 1440x900 is my max resolution. I am used to using 1600x1200 on my other PC (with radeon 7200) so I am just wondering if there is a way to get it higher than what it is at now, since this video card is much better than my old one, yet my old one seems to be able to display higher resolutions. maybe it is my screen? This laptop is brand new and my other moniter is 8 years old so I doubt that.

---

### Post by Nickay on 2006-07-14
gzilla i dont know if u had solved ur problem.
I had the same problem before and when i was trying to edit xorg.cong the file was empty!!!!!!

Try to boot in recover console and when u login type  
sudo dpkg-reconfigure xserver-xorg

Follow the instructions.
If u have the same problem again maybe u have problem with CardDispay drivers?

---

### Post by strabes on 2006-07-14
yeah that won't fix it. I just completely reformatted also and it's still not working. this 1024x768 on a widescreen is really really annoying. I've tried everything. easyubuntu, downloading the drivers from the ati site, doing the reconfigure thing, everything. Whenever i switch the driver to fglrx instead of vesa, when I reboot, X doesn't load and I have to do it again and re-select vesa.

---

### Post by fogster74 on 2006-07-14
> **strabes said:**
> I have the dell inspiron e1705 with radeon x1400 and I am trying to get my resolution above 1440x900. on a fresh install the max resolution was much lower than that, but I install the linux radeon driver and now 1440x900 is my max resolution. 

Strabes

The e1705 comes, as standard, with a WXGA+ screen which is maximum of 1440 x 900.

You would have to have paid extra for the WUXGA sxreen which runs at 1920 x 1200.

You may be able to run higher resolutions on an external monitor - but that can prove "fun"... see my post here for more info:

[http://www.ubuntuforums.org/showthread.php?t=214989](http://www.ubuntuforums.org/showthread.php?t=214989)

Fogster

---

### Post by strabes on 2006-07-14
Thanks for the info; glad I know that now. Except, while trying to get my resolution above 1440x900, I messed something up so I decided to reformat and start over again with a fresh install of ubuntu. Now, I can't seem to get my resolution above 1024x768 (on a widescreen) and I can't remember how I did it earlier. I can't seem to find a specific guide about installing drivers for radeon X1400 or getting my resolution higher. If you know what to do, please help me.

EDIT: I am no longer a noob and got this fixed a long time ago.

---

