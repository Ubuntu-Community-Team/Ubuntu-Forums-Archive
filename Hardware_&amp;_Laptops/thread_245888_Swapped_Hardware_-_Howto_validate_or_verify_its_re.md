---
title: "Swapped Hardware - Howto validate or verify its recognized?"
date: 2006-08-28
forum: Hardware &amp; Laptops
---

### Post by HeavyAl on 2006-08-28
Hey all,

Odd one for you here. I've been running Ubuntu on my IBM T40 Notebook since Dapper was released and recenty I had a problem that ended up causing me to have to replace the motherboard on the machine. The old motherboard had a faulty usb chipset which went from being recognized as usb1.1 (its supposed to be 2.0) to not being recognized at all and then on top of that the video card portion of the system (integrate ati 7500) decided to take a dump as well (read: it died horribly, thus needing to reoplace the board).

So, after finally getting a new board I swapped out the old one for the new one (in the process also adding another 512 megs to the system bring it up to a gig of ram, but thats probably not too important) and plugged in the drives and all the other junk that the system needs to run and booted her up. 

Amazingly the thing worked right away! Dapper seemed to think it was in the same system as before but with a few oddities that have me wondering if everything 'under the hood' is still working as it should be:

First, I used to just plug in the ethernet cable into the nic on the side of the t40 and ubuntu would automatically pull an ip address from the dhcp server - it still does this, but oddly enough it has switched from using eth0 to using eth1 - though this doesnt harm anything really as far as I can tell its just odd, and I hate things that dont have an explanation. Why did it decide that eth0 was no longer eth0 and now eth0 is eth1?? Incidentally, the nic is embedded on the t40 so maybe it has to do with the mac address being different? 

Second, after a couple of boots the auto-file-system-check decided it was time to run again and notified me that there were errors that couldn't be fixed without mounting read only and running fsck. Ok, no problem, I did that and everything seems to be fine - but what happened? Is this because I had to do all the component swapping and I banged the drive around causing it to have issues, or does it have to do with the new Motherboard some how?

Thirdly, how do I check to see if the USB is actually performing at 2.0 speeds? The ports definately work because I can plug a mouse into them and it finds it right away, but is there a tool that shows the status of usb hardware that I could use to check if these things are actually running as fast as they should?

Well, thats my (rather lengthy) story. If anyone has some thoughts I'd be happy to hear them. One thing I have to say though in closing is that Ubuntu definately rocks! If this was Windows I'd likely have been up all night having to reinstall the OS due to hardware compatiblity issues. It really saved me time to be able to basically plug Ubuntu back into the revamped machine and have it run as iif it had been there all along.

---

