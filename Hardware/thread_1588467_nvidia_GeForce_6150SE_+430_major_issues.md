---
title: "nvidia GeForce 6150SE +430 major issues"
date: 2010-10-04
forum: Hardware
---

### Post by OddJoe69 on 2010-10-04
Ok so I have not been having any luck with my video/sound card. I have tryed useing the alsa with no luck, just loose my sound and messes up the display. I have tryed calling nvidia about the problem, and got no help from them, as they told me they only offer support for windows. I just need thing issue fixed. I have very low volume, my mic fades out (the mic is brade new, as I replaced it thinking it was the problem not the soundcard). 

Nvidia GeForce 6150 +430 video/sound card
Ubuntu 10.04 LTS

If anyone knows how I can get the drivers for the video card working... When I tryed the linux nvidia drivers they did not work and had the same messed up results as alsa. Thanks for any help in advance...

---

### Post by NightwishFan on 2010-10-05
You will have to be more specific about what Ubuntu version my friend. :) Also I actually have this card and it works fantastically. Did you install the drivers from: System -> Administration -> Hardware Drivers?

As for alsa problems, please explain more symptoms.

---

### Post by OddJoe69 on 2010-10-05
Umm not sure how I can be more detailed about what Ubuntu I am running. Its Ubuntu 10.04 for the desktop thats avibale on there website. I went to System > Administration and dident see anything for hardware update or manager. You said you have the same video card....how did you get it working on your ubuntu?

---

### Post by NightwishFan on 2010-10-05
My apologies. I missed the Ubuntu 10.04 in the first post. This card is supported by Nvidia and the proprietary drivers in Ubuntu. Try installing the package nvidia-current in Synaptic. It should appear in hardware drivers regardless.

---

### Post by Cavsfan on 2010-10-05
Or you could do like I did and get the latest driver! I had that old one forever and thought I would try the latest 
I have not regretted it since! It is absolutely awesome!
[[COLOR=blue]_nVidia's latest drivers_[/COLOR]]("http://www.nvidia.com/Download/index.aspx?lang=en-us")

Just tell it what you have and go for it! You won't regret it!

---

### Post by cascade9 on 2010-10-05
> **Cavsfan said:**
> Or you could do like I did and get the latest driver! I had that old one forever and thought I would try the latest 
I have not regretted it since! It is absolutely awesome!
[[COLOR=blue]_nVidia's latest drivers_[/COLOR]]("http://www.nvidia.com/Download/index.aspx?lang=en-us")

Just tell it what you have and go for it! You won't regret it!

I dont think that complicating OddJoe69s issues by linking to the nvidia site is a good idea.....For 95%+ of ubuntu users, manually installing the nvidia drivers are pointless anyway.

---

### Post by Cavsfan on 2010-10-05
Oh I forgot to include these instructions I used and worked flawlessly!

[[COLOR=blue]_Instructions on how to install nVidia driver on Lucid._[/COLOR]]("http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html")

Supposedly you have to re-install the driver with every kernel update, but someone made a script to do that.
It worked for me and yesterday I "upgraded" from Lucid to Maverick and still have the latest driver! :P

I'll look for that post and put it here.

---

### Post by Cavsfan on 2010-10-05
> **cascade9 said:**
> I dont think that complicating OddJoe69s issues by linking to the nvidia site is a good idea.....For 95%+ of ubuntu users, manually installing the nvidia drivers are pointless anyway.

Things must have changed quite a bit in Ubuntu since the last time you tried to do this.
It works flawlessly and anyone (even me) can follow instructions. :P

---

### Post by Cavsfan on 2010-10-05
Here is the Howto for the script. 
It worked flawlessly for me and I am running nVidia driver version [COLOR=Red]260.19.06[/COLOR]
Way beyond 173 or 180 which is in the repositories.

[[COLOR=blue]_HOWTO: Automatically update manually installed NVidia drivers after kernel updates_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=835573")

You will just need to modify the driver file name to suit the commands. Piece of cake!
Anyone can do this as I am living proof. :P

---

### Post by cascade9 on 2010-10-05
> **Cavsfan said:**
> Here is the Howto for the script. 
It worked flawlessly for me and I am running nVidia driver version [COLOR=Red]260.19.06[/COLOR]
Way beyond 173 or 180 which is in the repositories.

[[COLOR=blue]_HOWTO: Automatically update manually installed NVidia drivers after kernel updates_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=835573")

You will just need to modify the driver file name to suit the commands. Piece of cake!
Anyone can do this as I am living proof. :P

nVidia-current on 10.04 is at 195.36.15, not 180 (173 is for older geforce FX cards)- 

[http://packages.ubuntu.com/lucid/nvidia-current](http://packages.ubuntu.com/lucid/nvidia-current)

260.xx drivers are still in BETA, so advising them is even more crazy than manually installing the last stable drivers (256.xx). 

Apart from people with cards unsupported by nvidia-current, or very, very, _very_ heavy gamers looking for an extra 1% increase in framerates, stick with the repo versions IMO.

---

### Post by Cavsfan on 2010-10-05
The drivers downloaded from that #5 post of mine are not beta. They are official. The version that **OddJoe69** would 
download is [COLOR=Red]256.53[/COLOR] released on August 31 2010.
My version was updated to [COLOR="Red"]260.19.06[/COLOR] with an update on Ubuntu Lucid.

And when I upgraded to Maverick yesterday it came along.

I believe it is up to the OP to determine what is the best choice and our job to provide him with possibilities.
There are plenty of people using these latest drivers with no issues.

---

### Post by OddJoe69 on 2010-10-06
Ok I installed the nvidia-current package. What do I need to do now. What config files do I edit, if any? What part of the config files do I edit? I have not done anything other then install the package yet. I havent even restarted the computer yet lol. Thanks again for the help everyone. Nvidia gave me no support what so ever, not on the phone, e-mail or there forums. I am deffently staying with linux and ubuntu.

---

### Post by NightwishFan on 2010-10-06
Sure, check under System -> Administration -> Hardware Drivers, and see if it is enabled. If not, do so and then reboot.

---

### Post by OddJoe69 on 2010-10-06
There is no System -> Administration -> Hardware Drivers. I fino lots of stuff under System -> Administration.... but not Hardware Drivers. Maybe I need to install something to activate it?

---

### Post by NightwishFan on 2010-10-06
You are using the Ubuntu Desktop correct, and not Xubuntu? If so, open a terminal and copy paste this command, and push enter:
```
sudo apt-get install jockey-gtk nvidia-common nvidia-173-modaliases nvidia-96-modaliases nvidia-current-modaliases
```

When prompted type your password, and if asked y or n press y.  If there are any errors post them here

When that is done go to system -> administration and look for hardware drivers.

---

### Post by OddJoe69 on 2010-10-06
ok I did that, enabled my video card and rebooted. When it rebooted it came up with a terminal login, which I logged in, then it opened the terminal and nothing else. I couldent get to my desktop, open firefox, anything. So I re-install ubuntu and ran the update manager (98 total updates).

---

### Post by NightwishFan on 2010-10-06
With the reinstall can you enable the driver? What is not working?

---

### Post by cascade9 on 2010-10-06
> **Cavsfan said:**
> The drivers downloaded from that #5 post of mine are not beta. They are official. The version that **OddJoe69** would 
download is [COLOR=Red]256.53[/COLOR] released on August 31 2010.
My version was updated to [COLOR=Red]260.19.06[/COLOR] with an update on Ubuntu Lucid.

And when I upgraded to Maverick yesterday it came along.

I believe it is up to the OP to determine what is the best choice and our job to provide him with possibilities.
There are plenty of people using these latest drivers with no issues.

There are people who are having issues with the 260.xx drivers, right here- 

[http://ubuntuforums.org/showthread.php?t=1588840](http://ubuntuforums.org/showthread.php?t=1588840)

253.xx is one thing, 260.xx beta is totally different. 

BTW, why bother moving from the 195.xx drivers? 

> **OddJoe69 said:**
> ok I did that, enabled my video card and rebooted. When it rebooted it came up with a terminal login, which I logged in, then it opened the terminal and nothing else. I couldent get to my desktop, open firefox, anything. So I re-install ubuntu and ran the update manager (98 total updates).

If that ever happens again, you can try the command 'startx' and hopefully the desktop should start.

---

### Post by Cavsfan on 2010-10-06
> **cascade9 said:**
> There are people who are having issues with the 260.xx drivers, right here- 

[http://ubuntuforums.org/showthread.php?t=1588840](http://ubuntuforums.org/showthread.php?t=1588840)

253.xx is one thing, 260.xx beta is totally different. 

BTW, why bother moving from the 195.xx drivers? 

I guess it is beta, I didn't know that! It works fine for me, but I understand there is an overheating issue for some people. 
I was used to the default nVidea drivers from hardware manager, but noticed I could update the driver to 253.xx and so I did.
Then it automatically went to 256.xx and to 260.xx with regular updates. They work a lot better than the default driver did.

And I don't have to re-install the driver with a kernel update with the script I was provided.

But, I guess maybe **OddJoe69** aught to stick with the driver from hardware manager.
That is up to him, but I did provide the driver download page, the how-to page for installing the driver and the script page for keeping it up to date.
And they all worked fantastic for me. My PC is a core 2 quad and my card is an nvidea Geforce 9800 GT 512MB.

---

