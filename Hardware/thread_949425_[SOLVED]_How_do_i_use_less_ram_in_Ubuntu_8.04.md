---
title: "[SOLVED] How do i use less ram in Ubuntu 8.04?"
date: 2008-10-16
forum: Hardware
---

### Post by henry_d on 2008-10-16
I have ubuntu 8.04 running on a laptop with 228mb ram and it seems to run ok as in you can move the mouse around and click on the menu, normally without lag but when you open a few programs it starts to slow down and takes a while to open the programs.

Whats things can i do to make 8.04 use less ram? and also is there a theme that doesn't use much memory as im using a custom theme and i thought maybe clearlooks might use less ram.

Any help would be appreciated

---

### Post by Helios1276 on 2008-10-16
Well if you go to the terminal and use the 'top' command, you will see a list of running processes which might help you determine better what is slowing you down. I'd imagine things like Emerald and Compiz would not help the situation. Also, Firefox can be a bit resource intensive at times, maybe have a look into a lighter browser?

---

### Post by felker2 on 2008-10-16
You can use less RAM by removing RAM from your system or by limiting the RAM used by using the boot option `mem='. ;-)

But seriously: [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements) specifies 384 MB as "recommended minimum requirements" (see below), so you have too little RAM to run Ubuntu reasonably well.

Solution 1: install more RAM. So: use *more* RAM instead of less RAM (as stated in your subject)
Solution 2: use Xubuntu instead of Ubuntu. I now run Xubuntu on my old 256 MB - 866 Mhz HP e-PC, that works quite OK. The machine can even run Firefox and VLC at the same time. ;-)

HTH


Recommended minimum requirements

Ubuntu should run reasonably well on a computer with the following minimum hardware specification. However, features such as visual effects may not run smoothly.

    * 700 MHz x86 processor
    * 384 MB of system memory (RAM)
    * 8 GB of disk space
    * Graphics card capable of 1024x768 resolution
    * Sound card
    * A network or Internet connection

---

### Post by snowpine on 2008-10-16
My recommendations are:
1) Install more ram. 384 is the minimum for Ubuntu 8.04; I personally would recommend 512mb or more.
2) Switch to a light-weight windows manager instead of Gnome. For example, 'sudo apt-get install openbox', then log out and at the login screen Options->Sessions->Openbox
3) Use lightweight applications instead of the defaults (Dillo, Links, or Epiphany instead of Firefox; Leafpad or Abiword instead of Openoffice; Thunar or PCmanfm instead of Nautilus, etc.)

Good luck!

---

### Post by henry_d on 2008-10-16
Thanks for the tips.

Will i have to go to options > sessions > openbox everytime i start the computer in order for it to not use gnome.

How does Openbox differ from gnome i.e. looks

---

### Post by eentonig on 2008-10-16
> **henry_d said:**
> Thanks for the tips.

Will i have to go to options > sessions > openbox everytime i start the computer in order for it to not use gnome.

How does Openbox differ from gnome i.e. looks

No, the first time you change this, it will ask you if you want to keep this for future logins as well.

---

### Post by henry_d on 2008-10-16
Are there any services i could disable to use less ram? I have already disabled bluetooth and printer.

---

### Post by OrangeCrate on 2008-10-16
Using a lighter distro, or WM, or adding RAM will help your situation, but do be aware, that no matter how much RAM you have, Linux will use it all.

Linux is different than Windows in that respect. See here for an explanation on how Linux uses RAM...

**Linux Memory Management, or 'Why is there no free RAM?'**

[http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?sid=619cda6e4dae2a0651c474f9f5e4dfcf](http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?sid=619cda6e4dae2a0651c474f9f5e4dfcf)

---

### Post by forcecore on 2008-10-16
Strange my ubuntu 8.04 takes only 124 mb memory on my esprimo v5535 with system log disabled (system works 100% fine), updates is disabled, bluetooth disabled, evolution things, remote desktop, system sounds. Everything is so fast because i disabled unneeded stuff.

---

### Post by snowpine on 2008-10-16
> **henry_d said:**
> Are there any services i could disable to use less ram? I have already disabled bluetooth and printer.

I'd recommend disabling the tracker search tool or whatever it's called. But I stand by my original comment: your computer does not meet the minimum system specs for Ubuntu, so the best things you can do are install more ram, try a different windows manager other than Gnome, and/or be selective with applications (use lightweight alternatives and don't have lots of apps running at the same time).

As far as Openbox is concerned, it's really easier to try it for yourself (it's not a big download) than for me to describe it. You can check out [www.box-look.org](www.box-look.org) to find some nice Openbox themes.

Good luck!

---

### Post by snowpine on 2008-10-16
> **forcecore said:**
> Strange my ubuntu 8.04 takes only 124 mb memory on my esprimo v5535 with system log disabled (system works 100% fine), updates is disabled, bluetooth disabled, evolution things, remote desktop, system sounds. Everything is so fast because i disabled unneeded stuff.

My Openbox installs tend to use around 30-60mb of ram at startup.

---

### Post by henry_d on 2008-10-16
> **forcecore said:**
> Strange my ubuntu 8.04 takes only 124 mb memory on my esprimo v5535 with system log disabled (system works 100% fine), updates is disabled, bluetooth disabled, evolution things, remote desktop, system sounds. Everything is so fast because i disabled unneeded stuff.

You say you have disabled updates. Do you have to enable it when you want to search for updates or do you just search for them?

---

### Post by Tomatz on 2008-10-16
On a laptop with those specs i would advise you use a lighter desktop enviroment, ie XFCE. Its pretty much the same as gnome (the default ubuntu desktop) but is designed for lower end systens with less ram.

You can install it with the following command **(_without_ effecting your ubuntu/gnome setup)**. Open a terminal and type:

```
sudo aptitude install xubuntu-desktop
```

Then once done (could take a while) press ***ctrl alt bkspace***. Then at the login window select **session**, then **xubuntu**.

Login

If you dont like it, post back and i will instruct you on how to remove it.

;)

---

### Post by OrangeCrate on 2008-10-16
> **henry_d said:**
> You say you have disabled updates. Do you have to enable it when you want to search for updates or do you just search for them?

If you disable automatic update checking, you can use apt-get to do the same thing. Frankly, that's my preferred way of updating my system, and I check daily for any updates.

```
sudo apt-get update
```

then,

```
sudo apt-get upgrade
```

Here's a tutorial/guide on apt-get. Pay particular attention to the "commands" area:

[http://wiki.linuxhelp.net/index.php/Apt-get_Guide](http://wiki.linuxhelp.net/index.php/Apt-get_Guide)

---

### Post by henry_d on 2008-10-16
I have a custom theme (shiki colours from gnome look). If i install xcfe will it keep this theme and will it keep all my wireless setings?.

Am i installing xubuntu or just the xcfu interface?

---

### Post by Tomatz on 2008-10-16
> **henry_d said:**
> I have a custom theme (shiki colours from gnome look). If i install xcfe will it keep this theme and will it keep all my wireless setings.

Am i installing xubuntu or just the xcfu interface?

You can use gnome themes in xfce but you will have to re-apply the theme once you install xfce to use it.

Yes this will install the full xubuntu(xfce) desktop alongside the ubuntu(gnome) desktop.

---

### Post by henry_d on 2008-10-16
Do you know what size the xcfe interface download will be?

---

### Post by forcecore on 2008-10-16
I do not update if system works fine 100%, lot of people suffer from problems when they update. I use mostly static software witout install or i collect offline .deb files if needed.

---

### Post by OrangeCrate on 2008-10-16
> **henry_d said:**
> Do you know what size the xcfe interface download will be?

I can't seem to find anything for you. Maybe someone else has the answer. As an aside, here's the instructions for adding the Xfce desktop to Ubuntu:

[http://psychocats.net/ubuntu/xubuntu](http://psychocats.net/ubuntu/xubuntu)

BTW, if you're not familiar with Asiyu's Psychocats site, it's a good one to bookmark, and read in it's entirety.

---

### Post by Onesimus on 2008-10-16
I have installed 8.04 on a machine with 256Mb of RAM (with no graphics card).  Once I disabled the visual effects, then I found that it was OK. Some applications were slow starting (e.g. OpenOffice), but once they were up and running things seemed to be OK. 

I didn't get much improvement installing XUbuntu.  

To disable the visual effects go to  System->Preferences->Appearance

[INDENT]Select the Visual Effects Tab, then select None.[/INDENT]

Hope this helps

---

### Post by henry_d on 2008-10-16
Yes that is helpful. I was just about to install the xcfe interface but i dont think i will know if it doesnt do much.

---

### Post by Tomatz on 2008-10-16
> **henry_d said:**
> Yes that is helpful. I was just about to install the xcfe interface but i dont think i will know if it doesnt do much.

Ran much faster than ubuntu on my old eeepc. If you install it and dont like it you can uninstall it (and all deps) like this:

```
sudo aptitude remove --purge xubuntu-desktop
```

For this to work you must use my previous command to install it.


;)

---

### Post by henry_d on 2008-10-16
Will i have to choose to start xcfe everytime i boot the computer?

---

### Post by snowpine on 2008-10-16
> **henry_d said:**
> Will i have to choose to start xcfe everytime i boot the computer?

It will ask if you want to make Xfce the default.

---

### Post by henry_d on 2008-10-16
If the xcfe interface works well do i use the remove command you posted but replace xubuntu with ubuntu to remove the gnome interface so i can save some space.

---

### Post by snowpine on 2008-10-16
> **henry_d said:**
> If the xcfe interface works well do i use the remove command you posted but replace xubuntu with ubuntu to remove the gnome interface so i can save some space.

Here's how to remove the Ubuntu packages and get "pure" Xubuntu:
[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

---

### Post by henry_d on 2008-10-16
To save me posting a new thread does anyone know why my internet download speed goes from fast to really slow into bytes. I have a netgear rangemax wpnt511 pci card

---

