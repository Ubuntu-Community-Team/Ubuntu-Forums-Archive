---
title: "Download airport-utils package to disk?"
date: 2008-09-22
forum: General Help
---

### Post by TomDaBomb2u on 2008-09-22
Hello,

I just built a computer and installed Ubuntu 8.04. I have an existing AirPort Express network, which the Ubuntu box does not see. I read that I need the package "airport-utils" in order for the computer to recognize the network. Since I cannot get online to download it, is there a way that I can download the package, burn it to a disc, then install it on the host computer???

Please help!
Thanks!
-Thomas

---

### Post by Taxman415a on 2008-09-22
Yes, if you open synaptic and mark the package you want to install for installation, then go to the File menu and select Generate package download script. You can then copy that file and paste the URLs into a browser and download the packages you need.

---

### Post by TomDaBomb2u on 2008-09-23
> **Taxman415a said:**
> Yes, if you open synaptic and mark the package you want to install for installation, then go to the File menu and select Generate package download script. You can then copy that file and paste the URLs into a browser and download the packages you need.

Thanks Taxman! I'm still a little unclear on the process though. I saved the script to my desktop as airport-utils.sh. So I run this script, and it's supposed to download the package to a file or something? I opened the script in a text editor, and it was just this ```
#!/bin/sh
```

Any ideas?

-Thomas

---

### Post by Taxman415a on 2008-09-23
You must not have marked the package for installation first. First you find the package you want then double click on it to mark it to install (or right click and select mark for installation.). Only then generate the script and then it should contain the URLs you need.

And yeah that script can then be run on a Linux system to download the files you need, but the real advantage for you is that it contains the URLs you need and you can open up the script and copy and paste those into a browser in any operating system and get the files you need, then copy those back over to your Ubuntu system.

---

### Post by lintoon on 2008-09-23
How about plugging a network cable from your pc into your airport.  You should have been supplied one with the airport and from your isp.

If you cannot do this I don't see any reason why you cant download it on another pc, burn it to disc then install it on your ubuntu box.

I thought the airport is just acting as a wireless access point.  If that's the case you may have a wireless issue on your pc.

I'm just guessing here because I've never seen it, BUT, is the airport utils package only for configuring the airport just like the apple utility.  It's just a thought.

---

### Post by TomDaBomb2u on 2008-09-29
> **Taxman415a said:**
> You must not have marked the package for installation first. First you find the package you want then double click on it to mark it to install (or right click and select mark for installation.). Only then generate the script and then it should contain the URLs you need.

And yeah that script can then be run on a Linux system to download the files you need, but the real advantage for you is that it contains the URLs you need and you can open up the script and copy and paste those into a browser in any operating system and get the files you need, then copy those back over to your Ubuntu system.

I have the package installed on my computer already, but not on the new one I'm building. That one doesn't have internet access at all.

@lintoon

> If you cannot do this I don't see any reason why you cant download it on another pc, burn it to disc then install it on your ubuntu box.

This is what I'm trying to do. Just so I'll know how to do it in the future. Can I download a package from one computer, burn it to a disc or copy to a flash drive, then install it on another computer, which is not connected to the internet?

Thanks for all your help!

---

### Post by TomDaBomb2u on 2008-09-30
OK so apparently, I'm dumb. I just downloaded the airport-utils_1-6_all.deb file from [http://packages.ubuntu.com/hardy/net/](http://packages.ubuntu.com/hardy/net/). I'm going to burn to a disc and install later. Thanks for your suggestions!

-Thomas

---

### Post by lintoon on 2008-09-30
You're on your way.  Good luck

---

### Post by Taxman415a on 2008-10-01
> **TomDaBomb2u said:**
> OK so apparently, I'm dumb. I just downloaded the airport-utils_1-6_all.deb file from [http://packages.ubuntu.com/hardy/net/](http://packages.ubuntu.com/hardy/net/). I'm going to burn to a disc and install later. Thanks for your suggestions!

-Thomas

Yes you can always do this. The reason I didn't tell you to do that is the method I gave you handles dependencies better. If there are other dependencies needed to install the package the script will get them too. And yes you have to follow the method's steps on the computer that needs the package installed. Otherwise you won't get the script output that includes the packages you need.

The other problem that comes in is when the package information on your non-networked computer gets out of date so much that the packages it looks for are no longer the current versions available. I don't have an easy way to go about downloading that information offline and updating it.

---

