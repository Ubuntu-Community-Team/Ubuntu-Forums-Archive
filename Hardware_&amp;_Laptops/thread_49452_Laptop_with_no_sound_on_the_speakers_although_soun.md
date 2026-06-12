---
title: "Laptop with no sound on the speakers although soundcard works"
date: 2005-07-16
forum: Hardware &amp; Laptops
---

### Post by ichi on 2005-07-16
Hi, 
 
I have a really strange problem with my new laptop (Medion MD-95022 basically a relabeled MSI S250). The sound card (sis7012) is supported by the alsa drivers and works (although only if I switch acpi off at boot time), but I cannot manage to make the built in speakers working. 
When I plug in a headphone it works just great, but the speakers stay silent all the time. 
It shouldn't be a hardware problem, since they work under MS Windows. I've even tried some live CD linux versions (slax, knoppix suse), but they produce the same result. 
I''ve set everything I could find to the maximum in kmix and in alsamixer. Nothing happened.

What am I doing wrong ? Anyone with similar problems, or even with a solution ? 
 
 Thanks! 
 
 Gyula

---

### Post by toastedd on 2005-08-23
I have the same problem! Any help please? 

I've searched Ubuntu forums only came up with this: [http://ubuntuforums.org/showthread.php?t=27466&highlight=laptop+speakers](http://ubuntuforums.org/showthread.php?t=27466&highlight=laptop+speakers), which is not helpful.

---

### Post by legendx on 2005-08-30
Hi,
     i've find my way out of this kind of problem wirh my ac'97 chip. Open "Volume control" in gnome and goto "edit" "preference". Then, click on "External Amplifier". At the end, you will be able to enable External Amplifier in the "Switches" tab in gnome volume manager. It work for me ...

---

### Post by legendx on 2005-08-30
Hi,
     i've find my way out of this kind of problem with my ac'97 chip. Open "Volume control" in gnome and goto "edit" "preference". Then, click on "External Amplifier". At the end, you will be able to enable External Amplifier in the "Switches" tab in gnome volume manager. It work for me ... :wink:

---

### Post by laffreyd on 2005-08-30
I had the same problem with my HP nx6120. I needed to use the 'alsamixer' utility to disable 'headphone jack sense' and/or 'line jack sense'.

Hope that works.

---

### Post by carey on 2005-08-30
[QUOTE=legendx]Hi,
     i've find my way out of this kind of problem with my ac'97 chip. Open "Volume control" in gnome and goto "edit" "preference". Then, click on "External Amplifier". At the end, you will be able to enable External Amplifier in the "Switches" tab in gnome volume manager. It work for me ... :wink:[/QUOTE]

Thanks!! This worked just great.

I wonder why Ubuntu didn't do this by default? My laptop speakers were completely silent before this... what does this option do anyway and why should it be turned on by default which makes my speakers not work?

---

### Post by JoostWestra on 2006-05-04
This doesn't solve the problem for the S250.
See my bug report hope this can be fixed.
______________________________________________________________
I have a Medion 95264 Laptop (same as MSI S250) with an SIS 661MX chipset.
Only weak sound from the jack, no sound thrue speakers at all. I have External Amplifier turnt on.
This is a known problem also for other distributions.

The solution should be this:
[http://craig.copi.org/computers/ms-1013/](http://craig.copi.org/computers/ms-1013/)
So upgrading to alsa 1.0.10.

But right now I am using Ububtu 6.06 Beta and it still isn't working.
I thought that Ububtu 6.06 Beta allready used ALSA 1.0.10.

Changing this file:
/proc/asound/card0/codec97#0/ac97#0-0+regs
using this command:
echo 7a 2090 > /proc/asound/card0/codec97#0/ac97#0-0+regs
also doesn't work because the file seems empty in Ububtu 6.06 Beta

In older versions of ubuntu I did not have rights to change that file.

More information in the Forum from other users:
[http://ubuntuforums.org/showthread.php?t=49452&highlight=msi+sound+s250](http://ubuntuforums.org/showthread.php?t=49452&highlight=msi+sound+s250)
[http://ubuntuforums.org/showthread.php?t=168662&highlight=msi+sound](http://ubuntuforums.org/showthread.php?t=168662&highlight=msi+sound)

Hope this can be fixed before the final release.

---

### Post by jonnyfive on 2006-05-04
[QUOTE=legendx]Hi,
     i've find my way out of this kind of problem wirh my ac'97 chip. Open "Volume control" in gnome and goto "edit" "preference". Then, click on "External Amplifier". At the end, you will be able to enable External Amplifier in the "Switches" tab in gnome volume manager. It work for me ...[/QUOTE]

This worked great! Thanks guys. There was just a little bit of confusion. I had some trouble because once External Amplifier is added, you need to go to the tab and uncheck it.

---

