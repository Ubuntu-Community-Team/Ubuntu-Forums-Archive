---
title: "cant install ubuntu on pc connected to an lcd tv"
date: 2009-10-15
forum: Installation &amp; Upgrades
---

### Post by gordito on 2009-10-15
Hi all.

I am trying to install Ubuntu 9.04 on my pc.
I am not using a monitor, but i have a 32" lcd tv connected to my 4350 via a dvi->hdmi cable.

When i choose to istall ubuntu ot try without any changes, i get a flickering black screen.

What are my options now?

Thank you for your help!

---

### Post by dummy910 on 2009-10-15
Check your bios settings just to make sure your svideo port is allowed, then check out the following post here on ubuntuforums.org

[http://ubuntuforums.org/showthread.php?t=1149711&highlight=television&page=2](http://ubuntuforums.org/showthread.php?t=1149711&highlight=television&page=2)

it worked for me.

---

### Post by gordito on 2009-10-15
What does Svideo have to do with me?

I am talking about DVI--> HDMI connection.

---

### Post by Mark Phelps on 2009-10-17
My guess would be that you would need to use the restricted ATI drivers to connect via DVI to HDMI (due to the resolutions needed) and that the default open source drivers used during install can't handle that.

Would suggest you connect to a monitor for install and, afterward, install the ATI drivers and see if then, you can connect to the HDMI port on your LCD.

---

