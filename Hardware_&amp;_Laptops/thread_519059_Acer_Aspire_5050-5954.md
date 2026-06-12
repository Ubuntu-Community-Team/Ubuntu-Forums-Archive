---
title: "Acer Aspire 5050-5954"
date: 2007-08-06
forum: Hardware &amp; Laptops
---

### Post by chantron on 2007-08-06
Hey Guys,

I just bought an Aspire 5050 notebook. I'm having a hell of a time getting it working properly. 

I've got Ubuntu 7.04 installed running the 2.6.22-9 kernel. 

First of all theres the problem with ACPI. If I don't boot with the acpi=off flag, it will hang on "Loading ACPI Modules". This is sort of an important issue with a notebook as I have no idea how much of my battery I'm using when not plugged in. 

Second, my wired NIC doesn't work properly unless I add the noapic flag when booting. If I don't add that, the nic shows up and looks like it works until you try and actually use it. Set up via DHCP, it gets an initial IP from the router but packets do not go through. It works though when I add the noapic flag though.

Third, Wireless. This subject is probably the bane of the ubuntu community but I'm having problems with it. I followed a thread detailing how to get it working specifically for my notebook and it's wireless chipset. It didn't work though, dmesg showed that ndiswrapper was loaded and was using the right driver but was unable to start the device or something like that. 

I'm not exactly asking for help (though if anyone can offer any, thats awesome :D) but rather I'm looking to see if any other owners of an Aspire 5050 are having issues like mine. Searching the forums, the problems seem to be limited to sound not working which, funny enough, works fine for me (with the updated kernel anyhow :p). I feel like I'm the only one with an Aspire 5050 that doesn't work!

My gut instinct tells me that all of these issues are related to the ACPI issue but how exactly I'm not so sure. 

THANKS!
:lol:

---

### Post by chantron on 2007-08-07
Just a quick bump!

Any Aspire 5050 owners out there?

---

### Post by ugm6hr on 2007-08-07
Just to show you're not alone....

I have an Aspire 5051AWXMi, which is a 5050 variant.  However, it looks like Acer modified various components between different incarnations, so it's difficult to work out what's going on.

With wifi - mine is an Atheros 5005G (which is 100% compatible), but I think some have a 5006.... here's the compatibility list: [http://madwifi.org/wiki/Compatibility/Atheros](http://madwifi.org/wiki/Compatibility/Atheros)

My ethernet works fine too (without any configuration).

My sound just required a quick adjustment in alsamixer settings to get it working, similar quick fix for external microphone.  Although sound did break with the initial Feisty kernel update (2.6.20-16), I initially just returned to 2.6.20-15 rather than mess around with compiling alsa.  I've also now used the walkerk How-to to upgrade Feisty to the new Gutsy kernel (2.6.22-9), which has maintained the sound.

However, having fixed my suspend function by using s2ram --force (another How-to) with 2.6.20-15, I now find that doesn't work with 2.6.22-9, which doesn't bode well for Gutsy....

Sorry to hear you're having a much harder time :(

---

### Post by chantron on 2007-08-08
> **ugm6hr said:**
> Just to show you're not alone....

I have an Aspire 5051AWXMi, which is a 5050 variant.  However, it looks like Acer modified various components between different incarnations, so it's difficult to work out what's going on.

With wifi - mine is an Atheros 5005G (which is 100% compatible), but I think some have a 5006.... here's the compatibility list: [http://madwifi.org/wiki/Compatibility/Atheros](http://madwifi.org/wiki/Compatibility/Atheros)

My ethernet works fine too (without any configuration).

My sound just required a quick adjustment in alsamixer settings to get it working, similar quick fix for external microphone.  Although sound did break with the initial Feisty kernel update (2.6.20-16), I initially just returned to 2.6.20-15 rather than mess around with compiling alsa.  I've also now used the walkerk How-to to upgrade Feisty to the new Gutsy kernel (2.6.22-9), which has maintained the sound.

However, having fixed my suspend function by using s2ram --force (another How-to) with 2.6.20-15, I now find that doesn't work with 2.6.22-9, which doesn't bode well for Gutsy....

Sorry to hear you're having a much harder time :(

Thanks for the response.

Its gotten to the point where I'm almost fed up :p

I think I might see if I can return it and get a different notebook. 

I need to get Linux on my notebook and I just don't think its gonna happen with this notebook.

I've read that Acer messes with the DSDT of the machines... is there any way to fix the ACPI issues I've been having? Even if it requires compiling fancy kernels, I'll do it! The ACPI dev guys say that if it works in Windows and it doesn't work in Linux then its a bug. 

Thanks a lot.

---

### Post by rfariasbsb on 2007-08-12
same problems with acer 5050-4598

---

### Post by Skidpad on 2007-08-12
Its a shame - all of these Acer issues, I think they really make some sweet laptops.  :(

/hijack...

---

### Post by robertor on 2007-09-06
hi chantron!
I have an acer 5050-4835. And i had a lot of problems with wifi and acpi, mainly with acpi. The solution? I do a downgrade of bios. I was using 1.3309 and change for 1.3302. All the problems go out.
Greets!
Roberto

---

### Post by helwitch on 2007-09-06
I've got an aspire 5050-3785, and got wireless working by using the steps outlined [here]("http://ubuntuforums.org/showthread.php?t=512828"), with having first done 
```
sudo rmmod ndiswrapper
sudo apt-get remove ndiswrapper-utils
sudo rm -r /etc/ndiswrapper/
sudo rm -r /etc/modprobe.d/ndiswrapper
```, then rebooting, then going into package management, making sure everything related to ndiswrapper was removed (it was), then following the steps on the above site. At the end of the steps, after ```
sudo modprobe ndiswrapper
echo "ndiswrapper" | sudo tee -a /etc/modules
``` I also did ```
 sudo ndiswrapper -m
```
Still dunno how to make it recognize the battery tho!

---

### Post by aubreyisland on 2008-05-28
Here's how I got Ubuntu 8.04 on an Acer 5050.

[http://imaginecambio.com/2008/05/28/ubuntu-804-acer-aspire-5050-3371/]("http://imaginecambio.com/2008/05/28/ubuntu-804-acer-aspire-5050-3371/")

---

