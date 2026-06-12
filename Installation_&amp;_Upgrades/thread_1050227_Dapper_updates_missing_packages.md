---
title: "Dapper updates missing packages"
date: 2009-01-25
forum: Installation &amp; Upgrades
---

### Post by dougalkerr on 2009-01-25
I installed 227 updates today as requested by the system on my home laptop. The laptop is an ols Acer Travelmate 630 which I believe to be the cause of many mushaps I seem to go through when trying to 'update' my Dapper system.
When I rebooted I got a message about the xserver not working and after clicking on only two further dialogue boxes I was presented with the command line.
I am a Linux newbie and for the life of me I cannot understand why there is not something to put the system back the way it was as an option if things go wrong. Never mind I am not crowing about it because after a bit of searching the Internet I got a couple of lines of commands and got my x back.
I think the problem was my own fault for not disabling ENVY as told to but, I assumed I only had to do this if I was 'upgrading' and not simply applying updates.
Now the thing is although I have my desktop back I seem to be missing items from the menus with on of them being the Synaptic Package Manager and another being the Software Sources both from the Administration menu under Syetm.
How can I get these missing packages and others back. They may actually be on the laptop but just not being applied to the menu lists.
I think after all the bother I have had with any kind of updates applied to Dapper I will resort to the initial installation option of Grub and not apply any more updates whatsoever.
Does anyone else have similar problems. I have tried installing Xubuntu as I was told it was for using on older syetms like mine with a lack of resources espaecially graphics memory of only 16Mb and no way to install more memory or upgrade the graphics but, Xubuntu will not display the desktop even off the live cd. I did download the Xubuntu 8.10 iso but it still didn't display and there are no error messages to work with. It would be nice to see a list of hardware that Ubuntu and Xubuntu does not work with without some work. It would save an awful lot of hassle.
So any ideas of how to get the missing packages back onto my Dapper install guys (and gals)???
Thanks.

---

### Post by Sam Lars on 2009-01-25
Could you tell us more about the commands that you used to fix the graphics?

---

### Post by dougalkerr on 2009-02-08
I can't remember the exact commands as the paper notes I took were thrown out whilst tidying up but, they seemed regular commands like xorg.conf-reconfigure or something like that.
Anyways since then some malicious 'btopenzone' address came through on a post and when the post opened all I could get was this web page advertizing btopensone and I couldn't get rid of it. I couldn't get rid of it even when I rebooted and opened Firefox again the only web page I could get referred to this btopenzone.
Today I couldn't boot into Ubuntu anymore and did an install of Xubuntu through Windows XP which I am lucky that I dual boot with.
I would dearly love to do away with XP altogether but, for occasions that Ubuntu goes sour and I simply can't sort it out with my limited knowledge, it is a life saver.
I am still trying to get photos onto my laptop using Linux and I haven't managed yet. I do a fair amount with digital photos and can't spend too much time with the Linux problem and have to resort to XP. It's a shame like I have said in another post today because the Gimp is a good image tool. Sorry I am gettind away from your original request for info on the commands I used. I am getting to know X and the commands to use with it except when I can't get to the GUI then I am a bit lost. ENVY certainly sorts out a lot with my graphics and I think X amy be why Xubuntu won't finish booting but, I don't know the command line enough to get Xubuntu to boot to the desktop to ehlp myself. I am hoping you knowledgable guys will be able to shed some light on a very frustrating part of my Linux life...

---

### Post by Sam Lars on 2009-02-08
If you right click on the menu, can you edit it?  You could also run
```
alacarte
```
in a terminal or in Alt+F3.  Either way should get you to where you can edit the menu items.  See if they're just unchecked in there or something.

---

### Post by Sam Lars on 2009-02-08
Any reason why you're using Xubuntu?  Would Ubuntu or Kubuntu work?
Is the boot giving you the X errors and going to a terminal login?

---

### Post by zvacet on 2009-02-08
If you had Ubuntu desktop there is no reason not to have Xubuntu desktop even your graphic is minimal.Command is the same 

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by dougalkerr on 2009-02-08
I have had Ubuntu desktop but, never 8.10. If I go through the updates from Dapper to Intrepid Ibex then I eventually run into the same problem once version 8.10 is installed. I can't complete the boot. I get so far into the boot and the laptop just stops. No messages, nothing...

---

