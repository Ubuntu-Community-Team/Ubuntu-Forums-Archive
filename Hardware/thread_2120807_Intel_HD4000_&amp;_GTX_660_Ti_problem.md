---
title: "Intel HD4000 &amp; GTX 660 Ti problem"
date: 2013-02-27
forum: Hardware
---

### Post by frankbooth on 2013-02-27
Hi,

I've got a desktop PC with both Intel HD4000 integrated graphics (Intel i5 Ivy Bridge) and a discrete video card (Nvidia GTX 660 Ti).

My problem is that the discrete video card does not work under Ubuntu, but it works fine in Windows.

Additional Hardware Drivers in Ubuntu does not allow me to install any Nvidia drivers, and says that there aren't any available.

According to the output of *lspci | grep VGA*:
```

00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation Device 1183 (rev a1)

```
It seems that the discrete card is detected, but isn't in use.

Has anyone had similar problems, or tips that could fix my problem?

---

### Post by Rebelli0us on 2013-02-27
I used Synaptic and installed nvidia-current. Does that not work for you?

---

### Post by oldfred on 2013-02-27
I do not know if it is only laptops, but some have posted they could turn off Video in BIOS/UEFI.

But then you may need no modeset to boot.

       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

    
       # You may need headers first - meta package for 12.10 version:
sudo apt-get install linux-headers-generic

   Re: How To Install Nvidia Drivers [v8.1.2.12 by Bogan]. post 1126
[http://ubuntuforums.org/showthread.php?t=1743535&page=113](http://ubuntuforums.org/showthread.php?t=1743535&page=113)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)

---

### Post by frankbooth on 2013-02-28
> **Rebelli0us said:**
> I used Synaptic and installed nvidia-current. Does that not work for you?

Nope :/ did you do any additional changes in the settings?

---

### Post by typhoon_tip on 2013-02-28
First question: do you have two separate video output on your desktop PC ? If yes, can you disable the onboard graphic card in BIOS, connect the display to the NVIDIA discrete card and try to install it with:

```
sudo apt-get install nvidia-current
sudo nvidia-xconfig
```

Then reboot.

---

### Post by frankbooth on 2013-03-01
> **typhoon_tip said:**
> First question: do you have two separate video output on your desktop PC ? If yes, can you disable the onboard graphic card in BIOS, connect the display to the NVIDIA discrete card and try to install it with:

```
sudo apt-get install nvidia-current
sudo nvidia-xconfig
```

Then reboot.

Not sure if I understood your question correctly, but the discrete Nvidia card does not give any output and I have to use the integrated card to get a picture. 

The discrete card did give output when booting a LiveCD, if that could be of any help?

---

### Post by typhoon_tip on 2013-03-03
No what I meant was the physical connectors in the back of your Desktop: do you have _two_ or _only one_ ? If you have two, then you must be able to shut off the integrated video card from BIOS and proceed with install of the nvidia driver according to above procedure. If you have only one, then you must use Bumblebee to make things work.

Edit: if still not clear, post a picture of the back of your desktop, with all connectors in clear view.

---

### Post by frankbooth on 2013-03-07
> **typhoon_tip said:**
> No what I meant was the physical connectors in the back of your Desktop: do you have _two_ or _only one_ ? If you have two, then you must be able to shut off the integrated video card from BIOS and proceed with install of the nvidia driver according to above procedure. If you have only one, then you must use Bumblebee to make things work.

Edit: if still not clear, post a picture of the back of your desktop, with all connectors in clear view.

Sorry for the late reply, I didn't have physical access to the computer. 

Yes, indeed, the BIOS option was there. I thought I'd looked everywhere, but apparently it was well hidden (these new graphical BIOS' with Beginner-mode and Advance-mode are really confusing). 

It works as intended now, thanks buddy :).

---

