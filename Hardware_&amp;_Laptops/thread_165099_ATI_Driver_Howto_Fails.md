---
title: "ATI Driver Howto Fails"
date: 2006-04-24
forum: Hardware &amp; Laptops
---

### Post by Animortis on 2006-04-24
Alright, I don't have much to go on at the moment.

I have a bare, fresh install of Breezy and I'm trying to get the ATI drivers installed. I went though the wiki's instructions on how to install them, first through ATI's downloaded drivers instructions (Which failed miserably) and then the Ubuntu version of the drivers.

Both failed. The ATI driver howto (The one involving the .run file) gives a complete failure message on the command 'sudo module-assistant build,install fglrx-kernel',
"Bad luck, the kernel headers for the target kernel version could not be found and you did not specify other valid kernel headers to use". Pushing okay continues with more errors.

The instructions on the Ubuntu version of fglrx just fails, without error messages at all. Everything goes smoothly until I reset, when I do fglrxinfo that says I'm still using Mesa.

The only thing I can think of is the deb files for the ATI install are conflicting with the packages from Ubuntu.

Is anyone else having this problem with their ATI drivers?

---

### Post by jazzmuzik on 2006-04-24
There's a headers package you need to install. I think it's linux-kernel-headers.

---

### Post by incubus on 2006-04-24
Do you mind if I ask you your specs (which ATI card)?

Can you take a look at:
/var/log/Xorg.0.log

And maybe post your xorg.conf?

incubus

PS: After installing the drivers you switched "ati" to "fglrx" in your xorg.conf right?

---

### Post by Animortis on 2006-04-24
ATI Radeon 9800.

My xorg.xonf is at [http://pastebin.com/678253](http://pastebin.com/678253)

Going to try the headers install momentarily.

Edit: Headers install then attempting the ATI .deb install failed, still using Mesa.

---

### Post by jazzmuzik on 2006-04-24
What is the failure message? A Mesa error?

---

### Post by Animortis on 2006-04-24
Nope. On reboot, I do fglrxinfo and it says it's still using Mesa. Both processes work up until that point.

---

### Post by adamkane on 2006-04-24
You'll mess up your system if you install linux-headers by itself.

You have to install these at the same time:
linux-686 linux-image-686 linux-headers-686 linux-restricted-modules-686

or these:
linux-k7 linux-image-k7 linux-headers-k7 linux-restricted-modules-k7

Reboot.

If you only install a single piece, you'll end up with a mixed installation, and you'll have inexplicable problems, when you try to install other packages.

---

### Post by mjziegle on 2006-04-24
Umm... This is a little bit of misinformation here.  Assuming you're using apt this isn't possible.

linux-headers is source code 
linux-restricted-modules are some very specific no freedriver modules one is fglrx
linux-686 will include a kernel and a boot image.

You can install pieces and parts with no problems.  Apt won't allow you to install conflicted versions.

In short you can't "mess up" the system by installing any one of these on its own.


-Matt

[QUOTE=adamkane]You'll mess up your system if you install linux-headers by itself.

You have to install these at the same time:
linux-686 linux-image-686 linux-headers-686 linux-restricted-modules-686

or these:
linux-k7 linux-image-k7 linux-headers-k7 linux-restricted-modules-k7

If you only a single piece, you'll end up with a mixed installation, and you'll have inexplicable problems, when you try to install other packages.[/QUOTE]

[QUOTE=Adler]Matt,

I followed the guidelines @ [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide), but generated my own .deb packages using the available ATI driver from here -- [https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=300](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=300).

I have a COMPAQ Notebook with the AMD 64-Bit Turion 2.2GHz chipset and am using the latest Dapper Beta with the x86_64, 2.6.15-20-amd64-k8 kernel, plus 2GHz of RAM. My experience is the opposite of yours. I had more trouble with the native UBUNTU fglrx components and that -- once I understood the correct guidelines -- I found that the .deb package install went well.

Also, there have been several changes to the ATI Driver over the past 2 weeks. I also see that the native UBUNTU Drivers have also been upgraded as of yesterday.

I think that either approach will get 2D going, but I keep asking myself how can you tell that we have -- either with the ATI Driver or the UBUNTU fglrx coponents -- gotten to 3D acceleration?

Somewhere I did see that listed in one of the commands that I ran in Shell, but forget which one that was. LOL!

Maybe some one else will jump in here with their thoughts.[/QUOTE]

---

### Post by adamkane on 2006-04-24
Yes you can mix 386 with 686, but you should install 686 packages, if you use Intel hardware. Otherwise you'll end up with problems during installation of other packages and drivers. You better to give good all around advice, and not require the user to keep track of which package is 386 or 686.

---

### Post by Ensnared on 2006-04-25
The [howto](http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide) doesn't say it, but you have to install the proper headers, which you accomplish by doing this:```
sudo apt-get install linux-headers-`uname -r`
```

What architecture you have doesn't matter as much as the version of the kernel you're using - if you're using the default (e.g. 386) then you also need the headers for the 386 version, otherwise it won't work.

That being said, it's a good idea to use the proper kernel for your architecture, e.g. 686 for Intel Pentium and k7 for AMD. But the important part as far as driver installation goes is to have the appropriate headers for the version of the kernel you're actually using.

---

