---
title: "Asus EEEPC 1000H Intrepid HowTo"
date: 2008-10-30
forum: Hardware
---

### Post by surfed on 2008-10-30
*******************************************************************************************************************
eeeubuntu 8.10 was just released making this obsolete. [http://www.eeebuntu.org]("http://www.eeebuntu.org") 
*******************************************************************************************************************

> UPDATE
Version 2.0 of the ACPI scripts now have a control panel in System Menu. To update just use the command update instead of install when running the script.

Removed V 1.8.0 of the WIFI driver as some report issues, my guess is that it depends on your router model if they work or not.


So I just spent the last week or so trying to get everything to work on my eee and thought i share...

Warning: I am writing this from memory, English is not my native language and Murphies Law might apply, any feedback is welcome.
 
Status:
Everything works.
Battery life is five plus hours with mixed wifi on and off.
I assume that you know how to install and configure a Ubuntu System.

What you will need:
1 Asus EEEPC 1000 (901 should work too)
1 Bootable USB Stick with Ubu 8.10
1 wired internet connection
1 hours of your time (send wife with kids shopping)
Coffee, some

First install Ubuntu as you would normally. After you first reboot you will have a working wired internet connection. No Wifi at this point.

Setup the array.org repos for a custom eee Kernel:
```
wget http://www.array.org/ubuntu/array-intrepid.list
sudo mv -v array-intrepid.list /etc/apt/sources.list.d/
wget http://www.array.org/ubuntu/array-apt-key.asc
sudo apt-key add array-apt-key.asc
sudo apt-get update
```
Now we actually install the new kernel:

```
sudo apt-get install linux-eeepc linux-headers-eeepc
```
Lets remove our self from generic kernel updates

```
sudo apt-get remove linux-generic linux-image-generic linux-headers-generic linux-restricted-modules-generic
```


Install the ACPI scipts (they will overclock in performance mode to 1.7G and take care of wifi toggle Fn-Keys etc):

[http://www.informatik.uni-bremen.de/~elmurato/EeePC/Intrepid_ACPI_scripts-EeePC_900A_901_1000.tar.gz]("http://www.informatik.uni-bremen.de/~elmurato/EeePC/Intrepid_ACPI_scripts-EeePC_900A_901_1000.tar.gz")

```

tar xfvz Intrepid_ACPI_scripts-EeePC_900A_901_1000.tar.gz
cd Intrepid_ACPI_scripts-EeePC_900A_901_1000/
chmod +x acpi-scripts.sh
sudo ./acpi-scripts.sh install
```

Uncomment the following line in /etc/acpi/eeepc/eeepc-actions.sh to enable Bluetooth:

```

/etc/acpi/eeepc/eeepc-bt-toggle.sh

```
 


Now edit /etc/default/acpi-support and enable Laptop Mode support:

```
ENABLE_LAPTOP_MODE=true
```
You might want to have a look at /etc/laptop-mode/laptop-mode.conf and edit to your liking, the file is well documented.

Now check and edit grub so that /boot/grub/menu.lst is configured to boot your eeepc kernel. 

```

sudo nano -w /boot/grub/menu.lst

```


To get 802.11n to work I had to configure my router to aes wpa2 only otherwise it would only connect at g speeds.

Thats it. Reboot and pray.

If you would like to install the netbook remix follow instructions here:

[https://launchpad.net/netbook-remix](https://launchpad.net/netbook-remix)


Now I dont take any credit for any of this,just putting it in one place, Thanks go out to:
ELMURATO for the acpi scripts 
ADAM for the custom kernel and 
THEMONO for the 1.8 wifi driver.
without them we would be stuck with Xandros or XP, kudos.

**FOR SUPPORT GO TO THIS FORUM:**

[http://forum.eeeuser.com/viewtopic.php?id=49865]("http://forum.eeeuser.com/viewtopic.php?id=49865")

---

### Post by doctorow on 2008-10-30
I have an Asus Eee 1000H with a 16GB SDHC card, on which I'd like to install a bootable Ubuntu 8.10, while keeping Win XP on my hard drive. Do you have any suggestions how I should proceed?

---

### Post by surfed on 2008-10-30
> **doctorow said:**
> I have an Asus Eee 1000H with a 16GB SDHC card, on which I'd like to install a bootable Ubuntu 8.10, while keeping Win XP on my hard drive. Do you have any suggestions how I should proceed?
 
 
I dual boot XP / Ubuntu but have both on my 160G Hard Drive. My approach would be to boot from usb, install to SDHC and make sure in the last step during install to click advanced and make sure that grub will be installed on your Hard Drive. Then you should be able to dual boot Xp on HD and UBU on SDHC.

---

### Post by doctorow on 2008-10-30
Thank you, luckily I still have a 8GB USB stick lying around... I'll do that (after making a backup of my Win partition).

Thanks again!

---

### Post by schwieb on 2008-10-30
> **surfed said:**
> 
Everything but Bluetooth toggle works. And I mean everything


Surfed,
Does bluetooth itself work, and just not the keyboard toggle? I gotta have my bluetooth!

---

### Post by surfed on 2008-10-30
Its just the toggle thats not working, you can still turn it on or off via the bios. Its a bug in the eee_laptop module but will be fixed soon i hope.

---

### Post by schwieb on 2008-10-30
That's awesome!  I might have to go ahead and switch from Hardy, even though it is working great for me.  I'm a sucker for the latest and greatest.

---

### Post by Glitch0r on 2008-10-31
Just to let you know. After installing 8.10 with this tutorial I was indeed able to get everything to work.

However, I'm unable to connect to any Wifi network. For none protected networks it tries to join but eventually fails and for protected networks it keeps asking for the password.

Thanx for your effort but I guess I have to wait till Ubuntu EEE is updated ... :(

---

### Post by surfed on 2008-10-31
> **Glitch0r said:**
> Just to let you know. After installing 8.10 with this tutorial I was indeed able to get everything to work.

However, I'm unable to connect to any Wifi network. For none protected networks it tries to join but eventually fails and for protected networks it keeps asking for the password.

Thanx for your effort but I guess I have to wait till Ubuntu EEE is updated ... :(

Are you sure your network configs are ok? As the network is detected, i dont think the problem is ubuntu but rather the setup. You could try wicd wifi manager, some have better luck with it but this method has worked on 3 eees so far.

---

### Post by martinjh99 on 2008-10-31
Followed this tutorial and everything works including camera and wireless.

When I shut the lid or logout and say suspend to ram nothing happens.  the screen flickers and then turns itself back on...

Any ideas?

---

### Post by Sollos on 2008-10-31
> **martinjh99 said:**
> Followed this tutorial and everything works including camera and wireless.

When I shut the lid or logout and say suspend to ram nothing happens.  the screen flickers and then turns itself back on...

Any ideas?

I have the same problem. It looks like Ubuntu can only suspend to disk, unfortunately. I sorely need this functin to increase the battery life!

---

### Post by surfed on 2008-10-31
Hmm, both suspend to Ram and Hybernate work perfectly for me. Maybe you can check your logs and see if there is anything of intrerrest. Are you running the 1000 or 901? Post your dmesg output after trying to suspend.

---

### Post by martinjh99 on 2008-10-31
[http://martinjh.homelinux.net/~martin/messages](http://martinjh.homelinux.net/~martin/messages)

Thats the tail of /var/log/messages after trying to hibernate.

I have a 901

---

### Post by surfed on 2008-10-31
> **martinjh99 said:**
> [http://martinjh.homelinux.net/~martin/messages](http://martinjh.homelinux.net/~martin/messages)

Thats the tail of /var/log/messages after trying to hibernate.

I have a 901

There is no usable output in your log, look for lines that start with PM and contain a lot of suspend entries.

---

### Post by martinjh99 on 2008-10-31
Sorry try again same link.

I'm running Kubuntu 8.10 KDE4.

---

### Post by redson on 2008-10-31
Thanks for this guide, used it with my 1000HA that came w/Windows XP and 160GB HD, most everything is working well, I noticed:

1) Mic is not working at least not with the Sound Recording app provided.  I'm not worried about this for the moment, so haven't looked into it.  Camera does work, installed and played around with Cheese for a bit.

2)  I did not install the wifi driver as specified, instead I installed linux-backports-modules-intrepid, as specified in a different thread.  I like to keep with standard packages as much as possible, so I'm using this as long as it works well enough.

If I disable the wifi, it sometimes won't work when you re-enable it.  i don't intend to disable wifi 99% of the time, so I'll just avoid this for the time being.

3) I had to edit grub to boot into the eeepc kernel w/out manually selecting it.  By default it still selected the -generic kernel.  This might be a side effect of dual booting XP?  If this is generally true and not just something I ran into it would be helpful to add it to the howto.

4)  There's screen flicker when the laptop is unplugged and screen brightness is turned down, has anyone else noticed this?  Defective hardware or just the way it is?

I haven't tried the SD card reader yet.

---

### Post by surfed on 2008-10-31
> **redson said:**
> T

2)  I did not install the wifi driver as specified, instead I installed linux-backports-modules-intrepid, as specified in a different thread.  I like to keep with standard packages as much as possible, so I'm using this as long as it works well enough.

If I disable the wifi, it sometimes won't work when you re-enable it.  i don't intend to disable wifi 99% of the time, so I'll just avoid this for the time being.



The Wifi Toggle is a bit of a hack, so if you go with a different driver, your mileage may vary. Also do not toggle wifi rapidly. I link to the 1.8.0 version of the wifi driver, the eeepc kernels from array come with 1.7.1. People are getting mixed results with those two, still not sure witch one is better but I am running 1.8 and get 130 down 65 up on 802.11n connections. (select aes wpa2 only in your router) 
To fix the grub issue, just uninstall generic kernel.
The mic... have to look into that.

---

### Post by rdd72123 on 2008-10-31
Hi!
I'm new to Linux and i've installed the Intrepid version on my EEEPC 1000H. So far i got everything to work, but i can't switch wifi on and off using the FN + F2 keys on my keyboard.
I followed all the instructions on this post, but it doesn't work. Am i missing something?
Where can i check it?

Thanks.

---

### Post by surfed on 2008-10-31
> **rdd72123 said:**
> Hi!
I'm new to Linux and i've installed the Intrepid version on my EEEPC 1000H. So far i got everything to work, but i can't switch wifi on and off using the FN + F2 keys on my keyboard.
I followed all the instructions on this post, but it doesn't work. Am i missing something?
Where can i check it?

Thanks.

The acpi scripts are just being worked on. Expect an update to this how to soon.

---

### Post by Narcoleptic on 2008-10-31
I've gotten 8.10 up and fully working, but the sound output through the speakers is a bit soft.  In 8.04.1 I was able to turn up the second slider in alsamixer (can't remember the exact label) and get passable sound but that slider is gone in 8.10.  Is there any way to boost the the sound output in 8.10?  I can barely hear even with the PCM audio turned up to 100%.

---

### Post by redson on 2008-10-31
> **redson said:**
> 
2)  I did not install the wifi driver as specified, instead I installed linux-backports-modules-intrepid, as specified in a different thread.  I like to keep with standard packages as much as possible, so I'm using this as long as it works well enough.

Hm, doesn't work well enough.   Wireless goes away after ~20-30 mins and then keeps asking me for my WPA password just installed the driver you suggested, we'll see if that's any better

---

### Post by surfed on 2008-11-01
> **Narcoleptic said:**
> I've gotten 8.10 up and fully working, but the sound output through the speakers is a bit soft.  In 8.04.1 I was able to turn up the second slider in alsamixer (can't remember the exact label) and get passable sound but that slider is gone in 8.10.  Is there any way to boost the the sound output in 8.10?  I can barely hear even with the PCM audio turned up to 100%.


Go to preferences in volume control applet and set LineOut to be visible.

---

### Post by surfed on 2008-11-01
> **schwieb said:**
> Surfed,
Does bluetooth itself work, and just not the keyboard toggle? I gotta have my bluetooth!

Blootooth works now, update to latest eeepc kernel and uncomment the eeepc-bt-toogle.sh line in /etc/acpi/eeepc/eeepc-actions.sh

---

### Post by Glitch0r on 2008-11-01
> **redson said:**
> 
3) I had to edit grub to boot into the eeepc kernel w/out manually selecting it.  By default it still selected the -generic kernel.  This might be a side effect of dual booting XP?  If this is generally true and not just something I ran into it would be helpful to add it to the howto.

This is probably exactly why my wifi didnt work correctly when I tried this tutorial. I used the instructions at [http://array.org](http://array.org) and now have everything working. But for the sake of this tutorial it would be good to add something about.

---

### Post by Narcoleptic on 2008-11-01
> **surfed said:**
> Go to preferences in volume control applet and set LineOut to be visible.

Crap.  Line Out was visible, and when I cranked it to 100% I lost all sound until I powered off.  I just tried it again and now I get full sound.  Thank you.

---

### Post by bunnybash on 2008-11-03
ok i am trying to get all this working on my 1000h... this is kind of annoying, as a linux noob, it is really really hard to get this stuff working.  

i have no idea how to even do these things mentioned at the start... i feel like 3 different steps are missing.

What does it mean "uncommment the following line"  where is the line?  what does uncomment mean??


Uncomment the following line in /etc/acpi/eeepc/eeepc-actions.sh to enable Bluetooth:

Code:

/etc/acpi/eeepc/eeepc-bt-toggle.sh



Now edit /etc/default/acpi-support and enable Laptop Mode support:

Code:

ENABLE_LAPTOP_MODE=true

---

### Post by surfed on 2008-11-03
> **bunnybash said:**
> ok i i am trying to get all this working... this is kind of annoying, as a linux noob, it is really really hard to get this stuff working.  

i have no idea how to even do these things mentioned at the start... i feel like 3 different steps are missing.

Uncomment the following line in /etc/acpi/eeepc/eeepc-actions.sh to enable Bluetooth:

Code:

/etc/acpi/eeepc/eeepc-bt-toggle.sh



Now edit /etc/default/acpi-support and enable Laptop Mode support:

Code:

ENABLE_LAPTOP_MODE=true

I did state "I assume that you know how to install and configure a Ubuntu System." so i did not include the commands on how to open a text editor. This is all experimental, geeky stuff, try the Tuvak approach.
Now a bit of knowledge: In configuration files to comment a line means to put the symbol # at the beginning of it, it will be ignored when run. To uncomment is to remove the "#" at the start of a line.

---

### Post by bunnybash on 2008-11-03
> **surfed said:**
> I did state "I assume that you know how to install and configure a Ubuntu System." so i did not include the commands on how to open a text editor. This is all experimental, geeky stuff, try the Tuvak approach.
Now a bit of knowledge: In configuration files to comment a line means to put the symbol # at the beginning of it, it will be ignored when run. To uncomment is to remove the "#" at the start of a line.

hahaha

yeah i know you stated that, but you gotta remember that installing ubuntu now can be dead easy... especially with wubi!!!

so it allows total newbs like me to feel that we have accomplished something when we in fact are not!!

Thanks for your help though, I now have everything running smoothly...  interesting point, i showed my wife ubuntu ibex last night and she asks "ummm can i get that, i really like the look of that!"

so tonight i will try installing it on her laptop!  

thanks for your help though and for allowing a newb into your party! :D  :guitar:

---

### Post by surfed on 2008-11-03
Good to know you figured it out. I did not mean to sound harsh, I do tech support, so i try to keep it down to a minimum during my free time....

---

### Post by francky_51 on 2008-11-11
Thanks surfed for this how-to :)
Everything is working fine except that I can't connect to hidden wireless network.

Is it a bug of networkmanager or of the wireless card driver ?

Is one of you having this problem too ?

Thanks

---

### Post by surfed on 2008-11-11
> **francky_51 said:**
> Thanks surfed for this how-to :)
Everything is working fine except that I can't connect to hidden wireless network.

Is it a bug of networkmanager or of the wireless card driver ?

Is one of you having this problem too ?

Thanks

I am having the same issue, problem is in the driver as i tried with WICD and got same results.

---

### Post by r00fus on 2008-11-11
Anyone know how to downgrade the wifi driver to 1.7.1?
I can't seem to find out where the driver is, and after upgrding to 1.8.0 (the rt2860sta-dkms_1.8LK_all.deb), it simply fails to detect or even show the wireless working.

The hardware tester does see there is a ralink card.

All I want to do is have wireless working (which it did before I upgraded to 1.8) :-)

---

### Post by ManFromMars on 2008-11-13
Ditto the post above (though to be fair, i didn't try the older drivers first, just jumped straight in with the newer ones, that'll teach me for not reading instructions properly).

Other than that, thanks for the instructions! All working well other than wireless hardware not being detected (though haven't tested Bluetooth).

---

### Post by surfed on 2008-11-13
1.7.1 is included in the eeepc kernel.
Be patient when toggling wireless, also I have experienced issues when booting with wireless off but if booted with wireless on everything works....

---

### Post by surfed on 2008-11-13
The acpi scripts now have a control panel where one can change the values for Fan Speed, Over / Under clocking, Custom Keys, toggling wireless, camera, flash reader etc

To update just use 
update 
instead of
install
when running the acpi install script.

---

### Post by r00fus on 2008-11-14
> **ManFromMars said:**
> Ditto the post above (though to be fair, i didn't try the older drivers first, just jumped straight in with the newer ones, that'll teach me for not reading instructions properly).

Other than that, thanks for the instructions! All working well other than wireless hardware not being detected (though haven't tested Bluetooth).

Mars,
I re-installed, and it wasn't the 1.8 drivers that caused my problem. Problem was installing the automatic updates after doing all the steps.  This time, I installed Intrepid, then got all the updates, then followed the eeepc kernel steps and all the following steps, and I have a completely working Ubuntu 8.10 setup with working wifi (haven't tested bluetooth).

---

### Post by surfed on 2008-11-14
remove all the non eeepc kernels to avoid breakage due to ubuntu updates.

---

### Post by r00fus on 2008-11-14
> **surfed said:**
> remove all the non eeepc kernels to avoid breakage due to ubuntu updates.

Surfed, doesn't one of the steps in the main post outline that?
```
sudo apt-get remove linux-generic linux-image-generic linux-headers-generic linux-restricted-modules-generic
```

Assuming that's the case, I still don't understand how my first install got fubar'd by the updates, as I did execute that step both times.

---

### Post by surfed on 2008-11-14
> **r00fus said:**
> Surfed, doesn't one of the steps in the main post outline that?
```
sudo apt-get remove linux-generic linux-image-generic linux-headers-generic linux-restricted-modules-generic
```

Assuming that's the case, I still don't understand how my first install got fubar'd by the updates, as I did execute that step both times.

It should, but if i remember correctly i just searched for kernel stuff in synaptic and removed everything from there so I never ran into this problem...

---

### Post by ManFromMars on 2008-11-15
> **r00fus said:**
> Mars,
I re-installed, and it wasn't the 1.8 drivers that caused my problem. Problem was installing the automatic updates after doing all the steps.  This time, I installed Intrepid, then got all the updates, then followed the eeepc kernel steps and all the following steps, and I have a completely working Ubuntu 8.10 setup with working wifi (haven't tested bluetooth).

Thanks for the tip :-) I'll give it a try tomorrow - haven't had Ubuntu installed for long so not much to lose from doing a fresh install.

---

### Post by ManFromMars on 2008-11-19
That seems to have done the trick - I'm now posting with my eee PC connected to the internet through a wireless network :-) Cheers!

---

### Post by t0dk0n on 2008-11-25
Hello... Everything pretty much works on my EeePC 1000 running Xubuntu 8.10. I do have problems with wifi, but I have 1.8.0 of the wifi driver. So, the only problem I cannot fix is quite annoying. I can't play from more than one audio source at a time. I have to stop MPD (My music player) in order to watch a flash video... Sometimes, I have to kill Firefox in turn to play my music again. I can't use skype while I play music, nor can I play video games and emulators with the sound output from those as well as music. It seems like it works fine on everyone else's Eee's, for I cannot find one mention of this issue anywhere. So, if someone could either clarify the status of ALSA on Eee's or show me how to fix it, I'd be very grateful. Should I perhaps replace ALSA with OSS4? 

One more question. Should I put a swap on my Eee? I noticed it works decently without one, but I don't want the flash drive to fail faster than it should just because of constant swap writes... I was considering putting one on my 16GB SD card, so I can at least replace that if it fails in the future...

---

### Post by lorenfb on 2008-12-06
> So I just spent the last week or so trying to get everything to work on my eee and thought i share...


You might consider this as a solution:

[http://cgi.ebay.com/Ubuntu-8-10-Installd-8GB-SDHC-Card-Asus-Eee-PC-901-1000_W0QQitemZ270311796682QQcmdZViewItemQQ](http://cgi.ebay.com/Ubuntu-8-10-Installd-8GB-SDHC-Card-Asus-Eee-PC-901-1000_W0QQitemZ270311796682QQcmdZViewItemQQ)

Although many might not like paying (find it objectionable) for a 
Ubuntu distro when most all are free, some do value time to tweak 
an install versus just spending for a "clean" install, i.e. $25/$50 
versus maybe hours/days of effort.

---

### Post by t0dk0n on 2008-12-07
> **lorenfb said:**
> You might consider this as a solution:

[http://cgi.ebay.com/Ubuntu-8-10-Installd-8GB-SDHC-Card-Asus-Eee-PC-901-1000_W0QQitemZ270311796682QQcmdZViewItemQQ](http://cgi.ebay.com/Ubuntu-8-10-Installd-8GB-SDHC-Card-Asus-Eee-PC-901-1000_W0QQitemZ270311796682QQcmdZViewItemQQ)

Although many might not like paying (find it objectionable) for a 
Ubuntu distro when most all are free, some do value time to tweak 
an install versus just spending for a "clean" install, i.e. $25/$50 
versus maybe hours/days of effort.


How do you know it's 100% compatible? Plus, it's just a live distro. You can't just install it. Two days of noob "tweaking", reading, and following instructions isn't worth any money when you can do it for free and buy an 8GB class 6 SD card for around $10. In fact, I think selling the distro and upping the price of an SD card is against the GPL code. So, whoever blows this money is totally getting ripped. I'll set the distro up for free for anyone. I'm not trying to flame you, but this is a terrible idea in my unhumble opinion.

---

### Post by dorame on 2008-12-07
Thank you, my 1000HA  160GB HD. It's small and comes with all the features :)

---

### Post by druellan on 2008-12-07
Hi surfed, thanks for the guide. Just a quick question:
I see that many users recommends elmurato scripts to manage ACPI and function keys. I'm currently using Greg's eee-control that is daemon based and seems to be fulfill the same function.
I'm wondering if there is something important I'm missing on those scripts in terms of performance and ACPI support.

Thanks again.

**Edit: **looking at laptop-mode.conf, some HardDisk tweaks seems to be a bit extreme for a non-SSD HD.

LM_AC_HD_IDLE_TIMEOUT_SECONDS=60
LM_BATT_HD_IDLE_TIMEOUT_SECONDS=60
NOLM_HD_IDLE_TIMEOUT_SECONDS=7200

60 seconds is way too low. Unless you have tweaked your OS for full memory usage, those values can make your HD to spin in and out almost constantly. IMHO this is not good for a not-solid HD.

1200 seems a more reasonable value to me.

LM_AC_HD_IDLE_TIMEOUT_SECONDS=1200
LM_BATT_HD_IDLE_TIMEOUT_SECONDS=1200
NOLM_HD_IDLE_TIMEOUT_SECONDS=7200

---

### Post by druellan on 2008-12-07
Mmmm thats odd, my HD is not using the CONTROL_HD_IDLE_TIMEOUT=1 alone but along with CONTROL_HD_POWERMGMT=1

The default values are:
BATT_HD_POWERMGMT=1
LM_AC_HD_POWERMGMT=254
NOLM_AC_HD_POWERMGMT=254

1 seems the value that causes a spin down of the HD every minute, so, I checked hdparm manual that says:
> 
Set Advanced Power Management feature, if the drive supports it. A low value means aggressive power management and a  high  value means better performance.  Possible settings range from values 1 through 127 (which permit spin-down), and values 128 through 254 (which  do  not  permit spin-down).  The highest degree of power management is attained with a setting of 1, and the highest  I/O performance  with a setting of 254. A value of 255 tells hdparm to disable Advanced Power Management altogether  on the drive (not all drives support disabling it, but most do).


Mmmm, not as clear as I wanted but I'm trying those values:
LM_AC_HD_IDLE_TIMEOUT_SECONDS=1200
LM_BATT_HD_IDLE_TIMEOUT_SECONDS=1200
NOLM_HD_IDLE_TIMEOUT_SECONDS=2400

BATT_HD_POWERMGMT=100
LM_AC_HD_POWERMGMT=254
NOLM_AC_HD_POWERMGMT=254

---

### Post by druellan on 2008-12-08
HD is still spinning off after 1 minute. Seems that IDLE_TIMEOUT params are not doing any effect to hdparm defaults. I'm switching it off until I get answers about that.

---

### Post by Skeorx13 on 2008-12-09
I have the 1000 40G but aside from the HDD the hardware is the same. I got wireless working for unsecured networks at school and I believe wep. I think some WPA networks I can connect to but not all. I am thinking they are WPA2. At home I have my landlord's password to his wireless (which I pay partly for). I have three other computers running wireless that can connect to it with no problem (one I just had to update the wireless drivers for the adapter I was using to access wpa2). With my EEE it just keeps asking for the password and won't connect. I am already using the ralink rt2860 drivers and eeepclean kernel. I tried searching here but the only thing I've found that I think might work I can't seem to find anymore. Anyone able to help me out?

---

### Post by lorenfb on 2008-12-10
"How do you know it's 100% compatible?"

Because I tested it!!!! Have You???????

"Plus, it's just a live distro. You can't just install it."

Really, having a problem reading? It's an INSTALLED version!

"Two days of noob "tweaking", reading, and following instructions isn't worth any money when you can do it for free and buy an 8GB class 6 SD card for around $10."

Yeah, when you value your time at the minimum wage or less, right!

"In fact, I think selling the distro and upping the price of an SD card is against the GPL code."

And where have you "learned" this?

"So, whoever blows this money is totally getting ripped."

In your opinion, but for those that lack a life other than PCs,
a DIY install and tweak is the "end all", right?

"I'll set the distro up for free for anyone."

O.K., so let's get with it! Here's a starter for you:

[http://forum.eeeuser.com/viewtopic.php?id=52600](http://forum.eeeuser.com/viewtopic.php?id=52600)

Help that guy out.

---

### Post by jmurrayil on 2008-12-10
> **t0dk0n said:**
> How do you know it's 100% compatible? Plus, it's just a live distro. You can't just install it. Two days of noob "tweaking", reading, and following instructions isn't worth any money when you can do it for free and buy an 8GB class 6 SD card for around $10. In fact, I think selling the distro and upping the price of an SD card is against the GPL code. So, whoever blows this money is totally getting ripped. I'll set the distro up for free for anyone. I'm not trying to flame you, but this is a terrible idea in my unhumble opinion.

I read the eBay listing, it IS an installed version.  Plus, the GPL does not restrict charging for services related to S/W.  Last, some people may rather spend a few dollars then read for hours on how to properly tweak their system - and then make a mistake that corrupts their OS F/S.

---

### Post by delphi on 2008-12-11
> **jmurrayil said:**
> I read the eBay listing...

Hi jmurrayil,

I'm sure you've read it and, since the seller's name is jmurray58, looks like you wrote it as well... ;)

Good luck with your venture and I, for one, hope it will help some people - just don't try (as above) too hard as it's not a good sport...

---

### Post by lorenfb on 2008-12-11
"just don't try (as above) too hard"

Do what? 

It's more appropriately labeled a clarification, hardly a "try too hard".

---

### Post by mrjohnsen on 2008-12-12
Hi! I've used this guide for my 1000h at everything works. Thanks! But I have some minor problems.

1) I got double soundcontrols with the Fn-keys. When I do a Fn + F12 etc the standard ubuntu sound control is invoked and so is the acpi script one. They are on top on each other and are adjusted differently in sync. How do I remove one of them? 

2) After I innstalled the scripts my hdd spins in/out constantly and makes annoying sounds. Possible to fix this? Is it bad for the hdd? 

Thanks.

---

### Post by surfed on 2008-12-12
> **mrjohnsen said:**
> Hi! I've used this guide for my 1000h at everything works. Thanks! But I have some minor problems.

1) I got double soundcontrols with the Fn-keys. When I do a Fn + F12 etc the standard ubuntu sound control is invoked and so is the acpi script one. They are on top on each other and are adjusted differently in sync. How do I remove one of them? 

2) After I innstalled the scripts my hdd spins in/out constantly and makes annoying sounds. Possible to fix this? Is it bad for the hdd? 

Thanks.


1) is eee-config installed? if yes remove it.
2) is laptop mode enabled and configured?
check /etc/default/acpi-support
and /etc/laptop-mode/laptop-mode.conf

For an up to date how to go here:
[http://forum.eeeuser.com/viewtopic.php?id=49081]("http://forum.eeeuser.com/viewtopic.php?id=49081")

---

### Post by mistakenkindness on 2008-12-12
I have not been able to get my wireless working on my 901 and it is driving me nuts.  I have included my ifconfig, iwconfig as well as uname -a.  If anyone has time to help a noob out I would greatly appreciate it.

```
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

$  ifconfig
eth0      Link encap:Ethernet  HWaddr 00:22:15:4b:b1:ac
          inet addr:xx.xxx.xxx.xxx  Bcast:xx.xxx.xxx.xxx Mask:xx.xxx.xxx.xxx
          inet6 addr: fe80::222:15ff:fe4b:b1ac/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3698 errors:0 dropped:0 overruns:0 frame:0
          TX packets:263 errors:0 dropped:0 overruns:0 carrier:3
          collisions:0 txqueuelen:1000
          RX bytes:313606 (313.6 KB)  TX bytes:48195 (48.1 KB)
          Interrupt:219

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)

$ uname -a
Linux mini-laptop 2.6.27-8-eeepc #1 SMP Sun Nov 16 12:02:12 MST 2008 i686 GNU/Linux

```Edit

While toggling the wifi button i ran a dmesg | tail and I am seeing errors but I do not understand them.

```

$ dmesg | tail
[  123.841178] ACPI Error (psparse-0530): Method parse/execution failed [\_SB_.PCI0.SBRG.EC0_.RCTP] (Node f7415ea0), AE_TIME
[  123.841462] ACPI Error (psparse-0530): Method parse/execution failed [\_TZ_.RTMP] (Node f741af30), AE_TIME
[  123.841720] ACPI Error (psparse-0530): Method parse/execution failed [\_TZ_.TZ00._TMP] (Node f741af90), AE_TIME
[  136.584065] pciehp: Card present on Slot(0-3)
[  137.588099] pciehp: No new device found
[  137.588126] pciehp: Cannot add device 0x1:0
[  197.993858] ATL1E 0000:03:00.0: ATL1E: eth0 NIC Link is Up<100 Mbps Full Duplex>
[  686.584069] pciehp: Card present on Slot(0-3)
[  687.588098] pciehp: No new device found
[  687.588125] pciehp: Cannot add device 0x1:0

```

---

### Post by esteckis on 2008-12-13
I am waiting for my EEE from UPS, I have read many posts and sites about trying out Ubuntu on the netbook.  There are some questions I have about formatting and installing.  From what I am reading in posts, with an ssd people are suggesting about reducing the read/write cycles on it (of course on another post, a military person states that the military has been using the ssd's for over 15 years because of the reliability (more shock resistant and much greater life span than a regular hard drive).

1) Ext/2 or Ext/3, The conflicting suggestion is to install Ubuntu using the ext/2 file system to cut down on on the usage of last time files were accessed.  Has there be a general consensus on which file system to use? Ext/2 or Ext/3?  Is Ext/3 more of a reliable format? Also since it has an atom processor, will using the Ext/2 be less processor intensive over all while I am using the Netbook?

2) If I install Ubuntu and have my home file on a USB or the on an SDHC card, what file system should I use on those items? I know the usb and other cards are normally formatted in FAT32? Can I format these in Ext/2? On my other windows desktop computers I have that program that lets you browse Ext/2 and Ext/3 partitions (explore 2fs)

Thanks for your help.

---

### Post by druellan on 2008-12-13
Lests wait for Surfed that has more knowledge than me, but my thought:

- If you enable the laptop-mode, read/write cycles should be reduced and the SSD's powersave mode enabled.
- I'm also thinking about change to ext2, but the truth is that with a little tweaking ext3 should run well an almost identical to ext2. Again, laptop-mode should address this pretty well.
- I have all my external cards formatted to FAT32 and I still have got no problems at all reading on both Linux or Windows.

---

### Post by esteckis on 2008-12-13
I just happen to be going through some more posts and I saw mentioned that the Intel Atom processor can handle 64 bit? Does this mean I can use The Ubuntu Intrepid 64 bit software?

[http://en.wikipedia.org/wiki/Intel_Atom]("http://en.wikipedia.org/wiki/Intel_Atom")

When I receive my EEE 1000 how can I check the processor type to see if it actually does have 64 bit capability?

I answered my own question, sorry people.

Atom N27x series (single-core)

[edit] "Diamondville" (45 nm)

    * All models support: MMX, SSE, SSE2, SSE3, SSSE3, Enhanced Intel SpeedStep Technology (EIST), XD bit (an NX bit implementation)
    * All models **DO NOT support: Intel 64 (Intel's x86-64 implementation)**, Virtualization Technology
    * Die Size: 25mm²
    * Package Size: 22mm × 22mm
    * Steppings: C0

---

### Post by Ronin609 on 2008-12-14
Well, in new to this whole linux thing, so bear with me here. I followed the instructions on this thread, but im still not seeing wireless, however i have gotten the eeepc options to appear.  When i click on it, nothing happens. :/ 

Here is what i put into terminal... mistakes included.

ronin@sweetpea:~$ wget [http://www.array.org/ubuntu/array-intrepid.list](http://www.array.org/ubuntu/array-intrepid.list)

--2008-12-13 23:22:14--  [http://www.array.org/ubuntu/array-intrepid.list](http://www.array.org/ubuntu/array-intrepid.list)

Resolving [www.array.org](www.array.org)... 72.167.46.68

Connecting to [www.array.org|72.167.46.68|:80](www.array.org|72.167.46.68|:80)... connected.

HTTP request sent, awaiting response... 200 OK

Length: 47 [text/plain]

Saving to: `array-intrepid.list'



100%[======================================>] 47          --.-K/s   in 0s      



2008-12-13 23:22:15 (1.02 MB/s) - `array-intrepid.list' saved [47/47]



ronin@sweetpea:~$ sudo mv -v array-intrepid.list /etc/apt/sources.list.d/

[sudo] password for ronin: 

`array-intrepid.list' -> `/etc/apt/sources.list.d/array-intrepid.list'

ronin@sweetpea:~$ wget [http://www.array.org/ubuntu/array-apt-key.asc](http://www.array.org/ubuntu/array-apt-key.asc)

--2008-12-13 23:24:03--  [http://www.array.org/ubuntu/array-apt-key.asc](http://www.array.org/ubuntu/array-apt-key.asc)

Resolving [www.array.org](www.array.org)... 72.167.46.68

Connecting to [www.array.org|72.167.46.68|:80](www.array.org|72.167.46.68|:80)... connected.

HTTP request sent, awaiting response... 200 OK

Length: 1795 (1.8K) [text/plain]

Saving to: `array-apt-key.asc'



100%[======================================>] 1,795       --.-K/s   in 0.004s  



2008-12-13 23:24:03 (407 KB/s) - `array-apt-key.asc' saved [1795/1795]



ronin@sweetpea:~$ sudo apt-key add array-apt-key.asc

OK

ronin@sweetpea:~$ sudo apt-get update

Get:1 [http://www.array.org](http://www.array.org) intrepid Release.gpg [197B]

Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg                   

Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US        

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg                

Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Translation-en_US     

Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release.gpg             

Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Translation-en_US  

Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Translation-en_US

Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Translation-en_US 

Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Translation-en_US

Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US

Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US

Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US

Ign [http://www.array.org](http://www.array.org) intrepid/eeepc Translation-en_US            

Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg [189B]

Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release

Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US       

Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US 

Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_US   

Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US 

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release                              

Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release                           

Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release [51.2kB]           

Get:4 [http://www.array.org](http://www.array.org) intrepid Release [2720B]                            

Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages                 

Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages           

Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Packages                     

Get:5 [http://www.array.org](http://www.array.org) intrepid/eeepc Packages [7261B]                     

Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources                  

Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources            

Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages             

Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources              

Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages           

Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources            

Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid/main Packages                     

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages                        

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Packages

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Sources

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Sources

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Packages

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Sources

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Packages

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Sources

Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Packages [237kB]

Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Packages [3861B]

Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Sources [74.1kB]      

Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Sources [1169B] 

Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Packages [27.4kB]

Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Sources [5727B]  

Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Packages [14B] 

Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Sources [14B]  

Fetched 411kB in 7s (57.7kB/s)                                                 

Reading package lists... Done

ronin@sweetpea:~$ sudo apt-get install linux-eeepc linux-headers-eeepc

Reading package lists... Done

Building dependency tree       

Reading state information... Done

The following packages were automatically installed and are no longer required:

  libfreebob0 menu linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic

Use 'apt-get autoremove' to remove them.

The following extra packages will be installed:

  linux-headers-2.6.27-8 linux-headers-2.6.27-8-eeepc

  linux-image-2.6.27-8-eeepc linux-image-eeepc linux-restricted-modules-eeepc

Suggested packages:

  fdutils linux-doc-2.6.27 linux-source-2.6.27

The following NEW packages will be installed:

  linux-eeepc linux-headers-2.6.27-8 linux-headers-2.6.27-8-eeepc

  linux-headers-eeepc linux-image-2.6.27-8-eeepc linux-image-eeepc

  linux-restricted-modules-eeepc

0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.

Need to get 29.0MB of archives.

After this operation, 124MB of additional disk space will be used.

Do you want to continue [Y/n]? sudo apt-get remove linux-generic linux-image-generic linux-headers-generic linux-restricted-modules-generic

Abort.

ronin@sweetpea:~$ y

bash: y: command not found

ronin@sweetpea:~$ tar xfvz Intrepid_ACPI_scripts-EeePC_900A_901_1000.tar.gz

tar: Intrepid_ACPI_scripts-EeePC_900A_901_1000.tar.gz: Cannot open: No such file or directory

tar: Error is not recoverable: exiting now

tar: Child returned status 2

tar: Error exit delayed from previous errors

ronin@sweetpea:~$ cd Intrepid_ACPI_scripts-EeePC_900A_901_1000.tar.gz

bash: cd: Intrepid_ACPI_scripts-EeePC_900A_901_1000.tar.gz: No such file or directory

ronin@sweetpea:~$ tar xfvz '/home/ronin/Desktop/Intrepid_ACPI_scripts-EeePC_900A_901_1000.tar.gz' 

Intrepid_ACPI_scripts-EeePC_900A_901_1000/

Intrepid_ACPI_scripts-EeePC_900A_901_1000/data/

Intrepid_ACPI_scripts-EeePC_900A_901_1000/data/de/

Intrepid_ACPI_scripts-EeePC_900A_901_1000/data/de/LC_MESSAGES/

Intrepid_ACPI_scripts-EeePC_900A_901_1000/acpi-scripts.sh

Intrepid_ACPI_scripts-EeePC_900A_901_1000/data/settings

Intrepid_ACPI_scripts-EeePC_900A_901_1000/data/eeepc-lvds-toggle.sh

Intrepid_ACPI_scripts-EeePC_900A_901_1000/data/eeepc-hotkeys

Intrepid_ACPI_scripts-EeePC_900A_901_1000/data/eeepc-wifi-control.sh

Intrepid_ACPI_scripts-EeePC_900A_901_1000/data/eeepc-vga-toggle.sh

Intrepid_ACPI_scripts-EeePC_900A_901_1000/data/eeepc-cardr-toggle.sh

Intrepid_ACPI_scripts-EeePC_900A_901_1000/data/eeepc-cam-toggle.sh

Intrepid_ACPI_scripts-EeePC_900A_901_1000/data/eeepc-bt-toggle.sh

Intrepid_ACPI_scripts-EeePC_900A_901_1000/data/temp.svg

Intrepid_ACPI_scripts-EeePC_900A_901_1000/data/fan.svg

Intrepid_ACPI_scripts-EeePC_900A_901_1000/data/eeepc-statusicon.desktop

Intrepid_ACPI_scripts-EeePC_900A_901_1000/data/eeepc-statusicon.py

Intrepid_ACPI_scripts-EeePC_900A_901_1000/data/eeepc-osd-daemon.py

Intrepid_ACPI_scripts-EeePC_900A_901_1000/data/eeepc-acpi-settings.svg

Intrepid_ACPI_scripts-EeePC_900A_901_1000/data/eeepc-acpi-settings.py

Intrepid_ACPI_scripts-EeePC_900A_901_1000/data/eeepc-fan-control.sh

Intrepid_ACPI_scripts-EeePC_900A_901_1000/data/eeepc-acpi-settings.desktop

Intrepid_ACPI_scripts-EeePC_900A_901_1000/data/eeepc-cpufreq-control.sh

Intrepid_ACPI_scripts-EeePC_900A_901_1000/data/eeepc-actions.sh

Intrepid_ACPI_scripts-EeePC_900A_901_1000/data/wlan

Intrepid_ACPI_scripts-EeePC_900A_901_1000/data/S99eeepc-restore

Intrepid_ACPI_scripts-EeePC_900A_901_1000/data/eeepc.conf

Intrepid_ACPI_scripts-EeePC_900A_901_1000/data/de/LC_MESSAGES/messages.mo

ronin@sweetpea:~$ cd Intrepid_ACPI_scripts-EeePC_900A_901_1000/

ronin@sweetpea:~/Intrepid_ACPI_scripts-EeePC_900A_901_1000$ chmod +x acpi-scripts.sh

ronin@sweetpea:~/Intrepid_ACPI_scripts-EeePC_900A_901_1000$ sudo ./acpi-scripts.sh install

[sudo] password for ronin: 

=============================================

= ACPI scripts - EeePC 900A/901/1000/1000H  =

= for Ubuntu 8.10 Intrepid Ibex             =

= v2.1                                      =

= by elmurato (GUI and OSD by Jan Hoffmann) =

=============================================



WARNING: Do not use these scripts with an unsupported model!



### Stopping processes...

=========================

Any  help would be greatly appreciated!!  I did manage to get my keyboard to work, so thats a plus.  I'll continue to test things out.
-Ronin

---

### Post by lorenfb on 2008-12-14
> I followed the instructions on this thread, but im still not seeing wireless, however i have gotten the eeepc options to appear. When i click on it, nothing happens.

When time is at a premium and viable results are required,
then consider this as a simple means to an end;

[http://cgi.ebay.com/Ubuntu-8-10-Installd-8GB-SDHC-Card-Asus-Eee-PC-901-1000_W0QQitemZ270311796682QQcmdZViewItemQQptZUS_Software?hash=item270311796682&_trksid=p3286.c0.m14&_trkparms=72%3A1205%7C66%3A2%7C65%3A12%7C39%3A1%7C240%3A1318%7C301%3A0%7C293%3A1%7C294%3A50](http://cgi.ebay.com/Ubuntu-8-10-Installd-8GB-SDHC-Card-Asus-Eee-PC-901-1000_W0QQitemZ270311796682QQcmdZViewItemQQptZUS_Software?hash=item270311796682&_trksid=p3286.c0.m14&_trkparms=72%3A1205%7C66%3A2%7C65%3A12%7C39%3A1%7C240%3A1318%7C301%3A0%7C293%3A1%7C294%3A50)

Have fun.

---

### Post by mistakenkindness on 2008-12-14
> **lorenfb said:**
> When time is at a premium and viable results are required,
then consider this as a simple means to an end;

[http://cgi.ebay.com/Ubuntu-8-10-Installd-8GB-SDHC-Card-Asus-Eee-PC-901-1000_W0QQitemZ270311796682QQcmdZViewItemQQptZUS_Software?hash=item270311796682&_trksid=p3286.c0.m14&_trkparms=72%3A1205%7C66%3A2%7C65%3A12%7C39%3A1%7C240%3A1318%7C301%3A0%7C293%3A1%7C294%3A50](http://cgi.ebay.com/Ubuntu-8-10-Installd-8GB-SDHC-Card-Asus-Eee-PC-901-1000_W0QQitemZ270311796682QQcmdZViewItemQQptZUS_Software?hash=item270311796682&_trksid=p3286.c0.m14&_trkparms=72%3A1205%7C66%3A2%7C65%3A12%7C39%3A1%7C240%3A1318%7C301%3A0%7C293%3A1%7C294%3A50)

Have fun.


If i wanted to get a disk and put it in and have it work right away I would have installed windows.  Half the fun of a Linux Box is getting it up and running your self.  Maybe you should take your advertisements someplace else.

---

### Post by surfed on 2008-12-14
eeebuntu 8.10 was just released, I recommend giving that a try.

---

### Post by lorenfb on 2008-12-15
> If i wanted to get a disk and put it in and have it work right away I would have installed windows.

Windows, what's that?

> Half the fun of a Linux Box is getting it up and running your self. 

For many of us, an installed & WORKING Ubuntu is a business
necessity and NOT a toy to play with.


> Maybe you should take your advertisements someplace else.

No, just bought it myself and trying to help others simplify
their lives by enjoying Ubuntu and not "fighting" it.

---

### Post by delphi on 2008-12-16
> **lorenfb said:**
>  trying to help others simplify their lives by enjoying Ubuntu and not "fighting" it.

Very touching. Now, instead of 'helping' others to spend their USD50 on what they can have for USD5 (USB key) and learn something (and making sure that they don't have to fork out another USD50 when they want to install a new version sometime in the future), how about at pointing them at the right places... 

Here, let me show you what I mean:

How to install Eeebuntu with a usb flash drive
( [http://www.liliputing.com/2008/12/how-to-install-eeebuntu-with-a-usb-flash-drive.html#more-3697](http://www.liliputing.com/2008/12/how-to-install-eeebuntu-with-a-usb-flash-drive.html#more-3697) )

---

### Post by lorenfb on 2008-12-16
- Buy versus DIY Ubuntu Installation Decision Analysis -

Variables;

W - hourly wage rate
T - time for DIY install (downloads, setups, tweaks)
P - purchase price of pre-installed Ubuntu install
C - cost of media (8GB Flash)

Decision Process;

If P < W x T + C then Buy

Initialization;

set P = $50, set C = $15 set W = $150/hr (for many businesses)

Solve;

if T > (P - C) / W then Buy

T > (50 - 15) / 150 ~= 14 minutes (dream on) for install 

For realistic DIY installation time, T ~= 2 hrs then;

If W < (P - C) /  T, then DIY

W < (50 - 15) / 2 = $17.50 / hr

So for those who value their time at less than $17.50/hr, 
the DIY installation makes for a rational decision, 
which is not the case for many!

---

### Post by druellan on 2008-12-16
If you are experiencing bad audio quality, low mic volume and reduced functionality on the gnome-volume-preferences, check this:

First, update your Alsa drivers to version 1.0.18a and up using the script here: [http://ubuntuforums.org/showthread.php?t=962695](http://ubuntuforums.org/showthread.php?t=962695) (* did not work for the lean kernel).

Then edit your alsa-base config file:
sudo nano /etc/modprobe.d/alsa-base

At the bottom of the file, add this line:
# eeePC 1000h patch
options snd-hda-intel index=0 model=basic

Reboot.

Your mixer should have now a volume slider for every output and input channel, including the mic boost control.

---

### Post by delphi on 2008-12-17
> **lorenfb said:**
> 
So for those who value their time at less than $17.50/hr, 
the DIY installation makes for a rational decision, 
which is not the case for many!

I assume that you're not being paid for spending your time (here and elsewhere)'helping' others by promoting the above commercial product - which, of course, doesn't make it a very "rational decision" in your own view :? Of course, I might be wrong and, in fact, you're financially involved. In which case I would remind you that spam is against the forum's rules... 


Now, most people would agree that a "rational decision" doesn't necessarily involve $ value. I'd suggest that spending 2hrs doing your own install is time well spent - not only you choose exactly how you want it done but also as it is more than likely that you're going to do it again sometime in the future with a newer version (in which case you would want to keep your /home partition intact...).

To paraphrase a well known proverb:
"Sell a man a fish and he eats for a day. Teach a man to fish and he eats for a lifetime." ...;)

---

### Post by Skeorx13 on 2009-01-20
> **Skeorx13 said:**
> I have the 1000 40G but aside from the HDD the hardware is the same. I got wireless working for unsecured networks at school and I believe wep. I think some WPA networks I can connect to but not all. I am thinking they are WPA2. At home I have my landlord's password to his wireless (which I pay partly for). I have three other computers running wireless that can connect to it with no problem (one I just had to update the wireless drivers for the adapter I was using to access wpa2). With my EEE it just keeps asking for the password and won't connect. I am already using the ralink rt2860 drivers and eeepclean kernel. I tried searching here but the only thing I've found that I think might work I can't seem to find anymore. Anyone able to help me out?
I got the newest updates for the eee kernel and what-not, removed the 1.8 version of the rt2860 driver in synaptic and went with the 1.7 driver (which is listed as the latest driver oddly enough). It didn't work but after shutting down for the night and starting up in the morning it now works with wpa2 wireless.

---

