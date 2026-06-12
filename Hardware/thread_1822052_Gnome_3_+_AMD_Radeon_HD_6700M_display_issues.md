---
title: "Gnome 3 + AMD Radeon HD 6700M display issues"
date: 2011-08-10
forum: Hardware
---

### Post by Faboul on 2011-08-10
Hi !

I've installed the 64 bit version of ubuntu natty on my laptop yesterday an ASPIRE 5742G.
I don't really like unity so i have installed UGR following these steps.( to be able to use GNOME 3 with ubuntu)
[http://ugr.teampr0xy.net/install](http://ugr.teampr0xy.net/install)

All worked fine.
My graphic card driver weren't installed yet.

Then i reached the time where i wanted to install my graphic card driver.
Using "Additionals driver" in the applications tab, i installed flgrx driver.
The display start being buggy.
I decide then to remove/purge everything and install instead the open source -ati driver, same problem ...

I join to this thread some screenshots of the notification icons that don't display properly.


I'm a beginner so if you need more information don't hesitate.

Thank you.

---

### Post by Faboul on 2011-08-10
here is another screen that might be helpful

---

### Post by .... on 2011-08-10
There are different configurations for ASPIRE 5742G. Post output of lspci so we know what video hardware you have:
```
lspci
```

---

### Post by Faboul on 2011-08-10
01:00.0 VGA compatible controller: ATI Technologies Inc Robson CE [AMD Radeon HD 6300 Series]
01:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]

Here it is, I have also problem with my audio driver i think, The sound on my laptop is pretty low and is not stereo ( sounds comes from the left only it's a bit weird ). If we can fix this in the same time it would be perfect :P

---

### Post by el_koraco on 2011-08-10
Gnome Shell don't work with fglrx yet. I wish you hadn't used the Additional driver utility, cuz it's gonna make everything harder. It didn't uninstall properly. Follow the steps outlined in this [article]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver"). The first method, then the second one if the first don't work. 

If you follow them, and end up booting to the command line, execute these commands one after another while in it (write it down on a piece of paper) - 

```
sudo mv /etc/X11/xorg.conf  /etc/X11/xorg.conf_old
sudo reboot
```Before you do anything, make a full backup of your data, as you might end up not getting out of the conundrum, thanks to the mess that is jockey-gtk, and you might have to reinstall.

---

### Post by Faboul on 2011-08-10
I already had a look in this article yesterday, when i followed a tutorial to install the open source ati driver they proposed this link to remove fglrx

I made things more simple this morning, i format my linux partition and reinstalled everything.
So now i have a brand new natty installation with gnome 3 (ugr again) and that's it.
My personal files are on a different partitions so no needs to backup. ;)

---

### Post by el_koraco on 2011-08-10
Excellent. 
check out the forums for news on AMD and Gnome Shell, then install the driver form the AMD site. It's very easy to install, and, more importantly, it uninstalls cleanly.

---

### Post by .... on 2011-08-10
> **Faboul said:**
> 01:00.0 VGA compatible controller: ATI Technologies Inc Robson CE [AMD Radeon HD 6300 Series]

That's a 6300 and you said you had a 6700. It's possible you have two graphics chips (hybrid graphics). ATI claims they support dual ATI hybrid with Catalyst 11.7, so it makes sense that the older driver that comes with 11.04 wouldn't work.

---

### Post by Faboul on 2011-08-10
I have really no idea what I have and that's the problem actually ... I bought this PC already setup in a super market ... with windows and a lot of useless crap preinstalled  ... So i decided to format everything and since then I have trouble with finding my graphic drivers. 

:/


Oh my ! I did a mistake in the title sorry ... It was the early in the morning when i've posted and i lacked a bit of sleep, i correct that :)

---

