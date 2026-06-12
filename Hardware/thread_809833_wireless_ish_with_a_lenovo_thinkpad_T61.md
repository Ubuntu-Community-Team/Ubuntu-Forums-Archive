---
title: "wireless ish with a lenovo thinkpad T61"
date: 2008-05-27
forum: Hardware
---

### Post by libby-martian on 2008-05-27
hi all

first thanks for the info already posted, it's nice to have help when you don't know what you're doing :)

my problem is this:  wired ethernet is fine, nothing special done after installing hardy to connect.  problem is wireless, I'm sure you've heard this all before.  I found the driver from [http://intellinuxwireless.org/?n=Downloads](http://intellinuxwireless.org/?n=Downloads) but having issues installing...

Intel pro wireless 3945ABG 802.11abg

thanks for the help!

---

### Post by CPImmanuel on 2008-05-28
Did you run a recent update? I am not sure that I remember how I installed that driver from Intel. I think I used make install, but after an update the wireless stopping working for me yesterday. I am back up by using the NDISWRAPPER and the Intel windows driver. That was pretty easy to install. Surprisingly, I find internet browsing to be much much faster than using the Intel Linux driver on my Thinkpad T61. 
If you are interested in trying out the NDISWRAPPER, install the wrapper, and then download the windows driver from Intel (all this assumes that your wired connection is working) and then just follow the instructions. You have to reboot to get it to work. 
If there are folks who know how to install the native Linux driver in a way that provides the same or faster performance than the NDISWRAPPER approach, please post ... Intuitively, I feel that the native Linux driver must have better performance, and I suspect that it was the way that I had it set up before (which I have now forgotten) that was causing the problem. I would also like to understand if anyone else had a problem with it failing. The only things that I did was 1. Run an update (via update manager), rebooted into a KDE 4 session where I realized it was not working. When I came back to my default GNOME session, it would try to connect to my wireless router, but it would always fail. All the settings appeared to be fine, and it was recognizing the hardware. After some frustration, I gave up and installed the NDISWRAPPER and the windows driver. 

Paul

---

### Post by libby-martian on 2008-05-28
hi Paul

thank you for your response, I appreciate it.  I hate to ask this of you though, would you please explain how exactly to type that into the console?  I haven't played around much with bash commands since I installed gutsy on my desktop at home months ago and pretty much forgot everything.  I've printed out lists of commands but the descriptions are so vague I don't know what to do with them.

more details on the laptop:  dual boot xp and hardy, wired ethernet works fine in hardy so I'm not totally w/o internet at least.  now for the pesky wifi ish...

merci bien!

---

### Post by CPImmanuel on 2008-05-28
Well, for using the NISWRAPPER, i did not use the console commands. I simply used add and remove application to install Windows Wireless Drivers which is an NDISWARPPER tool. Then I went to the intel site and downloaded the windows driver. I put the files in a directory and then used the windows wireless driver tool (It shows up under System--->Administration) and by trial and error found the .INF file which it accepted. For my t61, it is netw4x32.inf. I then configured it and it worked after I rebooted.

Hope this is helpful. 

Paul

---

