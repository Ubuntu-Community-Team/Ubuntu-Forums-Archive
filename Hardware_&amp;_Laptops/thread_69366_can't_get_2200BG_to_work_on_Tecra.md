---
title: "can't get 2200BG to work on Tecra"
date: 2005-09-26
forum: Hardware &amp; Laptops
---

### Post by mit on 2005-09-26
Hi,

I can't wait to use Ubuntu on my laptop so have been playing with the live CD :) 
I have looked in device manager and the Centrino wireless 2200bg is listed.
If i go in to Network settings it detects the name of my SSID :)  but even after typing the correct network key it fails to connect to it.
If it was a driver issue would it still find the SSID? I have looked at other threads but they seem to be when the wireless either isn't listed or won't work at all. 
Any pointers appreciated. :)

---

### Post by mlomker on 2005-09-26
> If it was a driver issue would it still find the SSID? 

What kind of encryption is it?  Can you shut it off as a test?

If it is WPA then you might have to use wpa_supplicant to get it to work.  If it is a hex key then you have to enter it as ascii and prefaced by **s:**.  Encryption gets complicated...it's best to shut it off for a bit until you're sure your drivers are working.

Here was a [recent reply]("http://www.ubuntuforums.org/showpost.php?p=368604") from me when I was helping someone set up ifplugd/wpa_supplicant and his wireless card.

---

### Post by mit on 2005-09-27
Hi,

Thanks for your reply. I will try it without encryption later and let you know the outcome. :)

---

