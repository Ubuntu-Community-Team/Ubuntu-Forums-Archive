---
title: "Linux in toshiba"
date: 2010-09-29
forum: Hardware
---

### Post by c00lwaterz on 2010-09-29
I have this toshiba m900 and until now im searching for some solution. I have tried many help from this forum. I also tried some linux distros. My issues is getting high temperature. The fan is not working. My laptop is new and working properly on windows. I have tried ubuntu, linuxmint, debian and i forgot some that I have tried. Im losing hope to use linux.

Can anyone suggest any linux that will work for my m900 toshiba with ati radeon hd 4500 series, core 2 duo 2.20ghz, 3gig memory, realtek rtl819se wireless lan.

Hope that there is some alternative than ubuntu that will work on my laptop(other linux).

pls enlighten me.. thanks in advance.

---

### Post by IcarusR on 2010-09-29
Have you tried a non debian distro ? ie slackware or suse ? 
Problem could be Debian related as I see all the distros you list that you've tried are Debian based.

---

### Post by c00lwaterz on 2010-09-29
> **IcarusR said:**
> Have you tried a non debian distro ? ie slackware or suse ? 
Problem could be Debian related as I see all the distros you list that you've tried are Debian based.

i have tried pcbsd, freebsd with same problem in other linux distros. 

opensuse and slackware i haven't tried. do they differ from ubuntu and other linux distro?

thanks for the reply

btw, I visit the slackware. How to get it? i don't know how. I have seen this [http://slackware.mirrors.tds.net/pub/slackware/slackware-13.1-iso/]("http://slackware.mirrors.tds.net/pub/slackware/slackware-13.1-iso/") but i don't know what to choose.

---

### Post by CLCressman on 2010-09-29
I have an older Toshiba with a dual core . Sometimes when I log onto my main user account my processor is running at a minimum of 50% and it starts getting hot. If I log out and back in it usually idles at 0% and cools back down. It does not have this problem in the other user accounts.

---

### Post by IcarusR on 2010-09-29
I'd go for the dvd.iso here, assuming you are x86 32 bit

[http://slackware.mirrors.tds.net/pub/slackware/slackware-13.1-iso/slackware-13.1-install-dvd.iso]("http://slackware.mirrors.tds.net/pub/slackware/slackware-13.1-iso/slackware-13.1-install-dvd.iso")

> opensuse and slackware i haven't tried. do they differ from ubuntu and other linux distro?


Don't know, you just listed all Debian variants.

Never tried Slack myself.

---

### Post by c00lwaterz on 2010-09-30
> **IcarusR said:**
> I'd go for the dvd.iso here, assuming you are x86 32 bit

[http://slackware.mirrors.tds.net/pub/slackware/slackware-13.1-iso/slackware-13.1-install-dvd.iso]("http://slackware.mirrors.tds.net/pub/slackware/slackware-13.1-iso/slackware-13.1-install-dvd.iso")



Don't know, you just listed all Debian variants.

Never tried Slack myself.

I think that file is not live. I want to test it first before install. I nearly damage my laptop in testing of many distros that will fit my laptop.

---

### Post by Peter09 on 2010-09-30
Have you tried this?
 
[http://ubuntuforums.org/showpost.php?p=9343968&postcount=218](http://ubuntuforums.org/showpost.php?p=9343968&postcount=218)

---

### Post by c00lwaterz on 2010-09-30
> **Peter09 said:**
> Have you tried this?
 
[http://ubuntuforums.org/showpost.php?p=9343968&postcount=218](http://ubuntuforums.org/showpost.php?p=9343968&postcount=218)

yes, im the one who ask for help with that post. it goes down but when i restart it goes hot again and again. the fan is not working properly on linux but i don't of all linux as i tried debian distros and pcbsd

---

### Post by Peter09 on 2010-09-30
Are you saying that the fix works, just that it does not stick between re-boots.

---

### Post by c00lwaterz on 2010-09-30
> **Peter09 said:**
> Are you saying that the fix works, just that it does not stick between re-boots.

i don't know. example the solution made it good but I try reboot then ok then after few minutes i try reboot then it goes terrible again. when i try reboot, I just observe without doing anything only the ubuntu forum to report it to some people that helps. then I post what i observe.

I have post thread the topic is "high temperature.." you can search it so you can see what we did and what solutions we tried.

---

### Post by girishadat on 2010-10-23
Dear CoolWaterz, I too was one of the posters in the forum you mentioned. I too own a Toshiba Portege M900. I had temperature problem and during that it reached even 90 or more degrees. But after the discussion we had, I had updated my BIOS version to the latest (it was 1.8, I updated it twice - 1.9 - issue solved here and now it is 2.5, I think). Also, I had to add something in grub.cfg to ignore the acpi state during booting.

Following is my grub menu entry.
```
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set 1410e9c6-81e9-437e-84fd-5d4cb4430ee0
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=1410e9c6-81e9-437e-84fd-5d4cb4430ee0 ro   quiet splash acpi.power_nocheck nomodeset video=uvesafb:mode_option=1280x800-24,mtrr=3,scroll=ywrap
	initrd	/boot/initrd.img-2.6.35-22-generic
}
```

**acpi.power_nocheck** is added to solve overheating.

Now I am posting this from my m900. Uptime is 2hrs plus and the CPU is at 50 degrees and the GPU is at 43 degrees. Also, I used to leave my laptop overnight, say for downloads or for Ubuntu version update to 10.10. ..etc.

Note that my m900 is a D3212 variant which was available in India during April 2010. It has got a graphic card nVidia GeForce G210M.

The problem I am facing is only with touchpad, which is using some default driver, and not the Synaptic one, and that is not allowing me to use the features of it fully, like multitouch. Also, sometimes it goes mad. :(

---

