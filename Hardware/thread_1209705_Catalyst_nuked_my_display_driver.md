---
title: "Catalyst nuked my display driver"
date: 2009-07-10
forum: Hardware
---

### Post by GringoMonkee on 2009-07-10
Hi all. 

Been lurking for a while but can't find an answer to this that isn't contradicted elsewhere:

Graphics driver is an ATI Radeon (X1950) off top of my head. Was experiencing lag issues with videos and GNOME visual effects so thought i'd found an answer in installing Catalyst to check the driver.

On reboot I am presented with a collection of white & black horizontal lines, and no o/s to speak of.

I can get into the terminal using recovery mode, but not sure what commands will flush out any display driver changes and revert me back to the vanilla driver that came bunded with the Jaunty live CD

Had a similar problem before and resorted to a re-install to get back to square one. Now i've been daft enough to do it again i figure i should try learn to fix it using terminal commands

Any help would be mucho appreciated

Gringo

---

### Post by GringoMonkee on 2009-07-10
Tried the following which got me back to square one,

apt-get remove xorg-driver-fglrx 
I guess what i need to know is, can i improve on the vanilla driver, and if so whats the best way to go about it without blowing up my O/S?

ta

---

### Post by SublimeBuntu on 2009-07-10
It happened to me too. I have a ATI all-in-wonder 9600 and post install the entire gui dies...

---

### Post by jocko on 2009-07-11
> **GringoMonkee said:**
> Graphics driver is an[COLOR=Red] ATI Radeon (X1950)[/COLOR] off top of my head. Was experiencing lag issues with videos and GNOME visual effects so thought i'd found an answer in installing Catalyst to check the driver.

> **SublimeBuntu said:**
> It happened to me too. I have a [COLOR=Red]ATI all-in-wonder 9600[/COLOR] and post install the entire gui dies...

Your cards are not supported by ati's proprietary driver anymore. Ati dropped support for everything older than the radeon HD 2000 series earlier this year, and their older driver does not support the xserver or kernel in jaunty.
So the open source drivers ("radeonhd" for the x1950 and "radeon" for the 9600) are the only drivers that support your cards.

---

### Post by gradinaruvasile on 2009-07-11
[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.12&lang=English)

---

### Post by GringoMonkee on 2009-07-11
thanks for the background guys. I assume my video performance on this card is as good as it's gonna get now? 

Or is there a way to do some tweaking through Flash settings etc?

Again, thanks.

---

