---
title: "4K Not Working"
date: 2017-01-19
forum: Hardware
---

### Post by july8six on 2017-01-19
Operating System
Ubuntu Studio 16.04

System Information
Monitor:  BenQ LCD Monitor BL2420U
Graphics Card:  EVGA    Geforce GTX 1050Ti

Issue
I have a BenQ monitor and I can't get all the resolution setting to work.   When I switch to the 4k option, everything appears tiny on the screen and I am unable to read it.  How do I get 4k to work properly on my monitor?

Steps I Have Taken
I called the company and their suggestion was for me to switch to Windows but they wouldn't give me a Windows key.

I then installed the Nvdia drivers off of the website and the monitor now is able to display most of the resolutions except for the 4k resolution, the screen is too tiny.

I switched from the 4k resolution back to the HD resolution.  Where I switch to the 4k resolution, I can't read what is on the screen.

Additional Question
I found a guide online but I don't know if it will work with my version of Ubuntu Studio because the guide is written in Kubuntu. Here are the instructions from the guide [https://www.girialam.com/2016/02/kub...-hidpi-screen/]("https://www.girialam.com/2016/02/kubuntu-and-hidpi-screen/"):

Finding the accurate DPI value is essential to find the accurate scaling value for the screen.First of all, we need to grep the connected screen: xdpyinfo | grep -B2 resolution.On my laptop, the output is:dimensions: 3200x1800 pixels (302x169 millimeters)
Since the value must be in inch, we then need to convert the value based on the output, so it is 302 ÷ 25.4 and then divide 3200 by 11.88. The result is 269. So this is it, the accurate DPI value for the 2015 HP Envy 13 is 269 DPI.By default, the DPI value in KDE is set to 96 DPI. To find the accurate display scaling value we need to divide the accurate DPI by 96, so it is 269 ÷ 96 which is 2.8.Now head to System Settings > Fonts > Force fonts DPI to set the DPI value and to System Settings > Display and Monitor > Display Configuration > Scale Display to scale the screen display, then re-login.After scaling the display the UI will looks rather odd where the icon seems too small, so we need to readjust the icon size, this must be done manually as KDE will not scale it automatically when non-integer value is set. Head to System Settings > Icons > Advanced and double everything in there.[[IMG]https://www.girialam.com/wp-content/uploads/2016/02/snapshot3-150x150.png[/IMG]]("https://www.girialam.com/2016/02/kubuntu-and-hidpi-screen/snapshot3/")
Screen Scaling[[IMG]https://www.girialam.com/wp-content/uploads/2016/02/snapshot6-150x150.png[/IMG]]("https://www.girialam.com/2016/02/kubuntu-and-hidpi-screen/snapshot6/")
Resizing Icons
Now, verify if the system is using the given DPI value with xdpyinfo | grep dots. Finally to make the changes survive system reboot, we need to create a file named 77set_dpi and enter xrandr --dpi 269x269 in /etc/X11/Xsession.d/$ nano /etc/X11/Xsession.d/77set_dpixrandr --dpi 269x269
Other best practice is to create .Xresources in /home/USER/, so that non DE&#8217;s applications will also use the given DPI value as well as other display configuration such as anti-aliasing and font hinting. My .Xresources parameter is as follows:Xft.dpi: 269
Xft.autohint: 0
Xft.lcdfilter: lcddefault
Xft.hintstyle: hintslight
Xft.hinting: 1
Xft.antialias: 1
Xft.rgba: rgb

---

### Post by howefield on 2017-01-19
Thread moved to the "*Hardware*" forum for your monitor issue.

Feel free to start a new thread in the [Networking & Wireless]("https://ubuntuforums.org/forumdisplay.php?f=336") forum for the wireless adapter question, one question per thread is best.

---

### Post by ian-weisser on 2017-01-19
Threatening to leave due to hassle (or any other reason) makes no difference to us. We are not your vendor, and you are not our customer.
Seems like you jumped the shark before you did proper research and testing, and now you're paying a price for that impulsive decision. At the moment, that price is your time.
One purpose of the LiveUSB installer is to test your hardware with Linux before installing.

I doubt you will find anyone willing to support hardware that they didn't make in a price range you consider 'affordable.' But we don't know what you consider 'affordable' to be - maybe there is.

Many of us had similar problems when we jumped the shark, too.
We figured out how to fix our problems, and you will also.

Yes, lots of hardware from shoddy manufacturers doesn't work well with Linux. Not our fault. Buy your hardware from reputable, Linux-supporting manufacturers. Lots of them around.
There may be workarounds for many of your issues, but you will need to provide much more information, like model numbers and chipsets and exactly what you have already tried.

Troubleshooting hardware is common enough that many subforums (like Networking and Wireless) have stickies detailing how to start the process. Find them and read them.
Once you figure out how to locate your model numbers and chipsets, use those for searching - lots and lots of unique, successful hardware solutions are already in these forums.

---

### Post by july8six on 2017-01-20
> Threatening to leave due to hassle (or any other reason) makes no difference to us. We are not your vendor, and you are not our customer.
I know it makes no difference to you.  I was venting a little.

> I doubt you will find anyone willing to support hardware that they didn't make in a price range you consider 'affordable.' But we don't know what you consider 'affordable' to be - maybe there is.
If you know of any please provide their websites and phone numbers instead of making an unhelpful remark.

> Many of us had similar problems when we jumped the shark, too. We figured out how to fix our problems, and you will also.
If this is a common problem, how come Ubuntu doesn't fix it?  How do I report these issues so they can get fixed in a later OS release?

> Yes, lots of hardware from shoddy manufacturers doesn't work well with Linux. Not our fault. Buy your hardware from reputable, Linux-supporting manufacturers. Lots of them around.
This is an unhelpful comment.  Gigabyle, AMD, Intel, and BenQ, and EVGA are not shoddy manufactures.

> There may be workarounds for many of your issues, but you will need to provide much more information, like model numbers and chipsets and exactly what you have already tried.
Where do I find my model numbers and chipsets?  I already said what I tried.  Please reread my OP:  I called the BenQ company and they told me to get Windows.  I called the company and their suggestion was for me to switch to Windows but they wouldn't give me a Windows key. I then installed the Nvidia drivers off of the website.

> Troubleshooting hardware is common enough that many subforums (like Networking and Wireless) have stickies detailing how to start the process. Find them and read them.  Once you figure out how to locate your model numbers and chipsets, use those for searching - lots and lots of unique, successful hardware solutions are already in these forums.
Can you please provide some links?

---

### Post by QIII on 2017-01-20
Hello!

I want to make a general comment about hardware, as you seem to be, like many, under a general misconception.

Nobody in the open source world can do much of anything to get hardware to work with Linux if the OEM does not provide drivers.  Canonical, which distributes Ubuntu, does not write drivers for hardware.  Neither, for that matter, does Microsoft -- except for their own branded hardware.

It is hardware OEMs who write driver software.

That drivers work with Windows is no indication that Microsoft does anything at all to make sure they work.  OEMs make sure their drivers work with Windows or they starve.  It's as simple as that.

They don't starve if they don't bother to make drivers for Linux.

Now, that all said, there are cases where open source developers are able to back-engineer into a black box and get some things to work fitfully.  But since those developers are working in black boxes, it is often the case that they produce nothing better than a kludge.

So:  Please approach hardware issues with that frame of reference.  Don't expect that hardware problems are necessarily the "fault" of Linux distributions.  Don't expect a newer release to fix hardware problems that the OEM does not fix.

Most of us have had issues with hardware at one time or another and are willing to share solutions and work arounds.  But if you have a complaint, take that to the OEM and ask why they don't have a Linux driver.  We can't do anything about that.

Keep this in mind and you will have a much more pleasant time as folks try to help you.

Thanks.

---

### Post by Yellow Pasque on 2017-01-20
Yes, text @ 4K looks very small on a 24" monitor, and it's going to look that way whether you're using Linux or Windows. 
The solution is to use scaling. See the "UI Scale" slider in the first screenshot: [http://www.phoronix.com/scan.php?page=news_item&px=MTYzMTM](http://www.phoronix.com/scan.php?page=news_item&px=MTYzMTM)
Scaling doesn't always work flawlessly and can take some tweaking on certain apps. (Again, same thing happens in Windows).

> I called the company and their suggestion was for me to switch to Windows but they wouldn't give me a Windows key.
You seriously expected a free Windows key?

---

### Post by july8six on 2017-01-23
> **Temüjin said:**
> Yes, text @ 4K looks very small on a 24" monitor, and it's going to look that way whether you're using Linux or Windows. 
The solution is to use scaling. See the "UI Scale" slider in the first screenshot: [http://www.phoronix.com/scan.php?page=news_item&px=MTYzMTM](http://www.phoronix.com/scan.php?page=news_item&px=MTYzMTM)
Scaling doesn't always work flawlessly and can take some tweaking on certain apps. (Again, same thing happens in Windows).


You seriously expected a free Windows key?
Yes.  If they want me to switch to Windows, I need a software key.

> **QIII said:**
> Hello!

I want to make a general comment about hardware, as you seem to be, like many, under a general misconception.

Nobody in the open source world can do much of anything to get hardware to work with Linux if the OEM does not provide drivers.  Canonical, which distributes Ubuntu, does not write drivers for hardware.  Neither, for that matter, does Microsoft -- except for their own branded hardware.

It is hardware OEMs who write driver software.

That drivers work with Windows is no indication that Microsoft does anything at all to make sure they work.  OEMs make sure their drivers work with Windows or they starve.  It's as simple as that.

They don't starve if they don't bother to make drivers for Linux.

Now, that all said, there are cases where open source developers are able to back-engineer into a black box and get some things to work fitfully.  But since those developers are working in black boxes, it is often the case that they produce nothing better than a kludge.

So:  Please approach hardware issues with that frame of reference.  Don't expect that hardware problems are necessarily the "fault" of Linux distributions.  Don't expect a newer release to fix hardware problems that the OEM does not fix.

Most of us have had issues with hardware at one time or another and are willing to share solutions and work arounds.  But if you have a complaint, take that to the OEM and ask why they don't have a Linux driver.  We can't do anything about that.

Keep this in mind and you will have a much more pleasant time as folks try to help you.

Thanks.
This is frustrating because I spend a lot of money on my monitor and my graphic's card.  I guess I will have to call back the companies tomorrow for a solution.

---

### Post by QIII on 2017-01-23
> **july8six said:**
> Yes.  If they want me to switch to Windows, I need a software key.

That switch will be at your cost.  You are not owed a key.

---

### Post by Yellow Pasque on 2017-01-23
Good luck with that.
Unsubscribing...

---

### Post by july8six on 2017-01-24
> **QIII said:**
> That switch will be at your cost.  You are not owed a key.
Companies should be honest with their advertising and put "Windows Compatible Only" in their product descriptions and product boxes.  I wish one day someone would file a class action lawsuit against companies who do not advertise their products correctly.  I am not a big fan of deceptive advertising.  If I buy a monitor or graphics card it should say on the product description and box it will only work with Windows machines.  This information should be readily available to the consumer when making buying choices.  They should also provide the software needed to get their products to work if they don't indicate the software requirements on the box, marketing materials, etc.

I found a guide online but I don't know if it will work with my version of Ubuntu Studio because the guide is written in Kubuntu.  Here are the instructions from the guide  [https://www.girialam.com/2016/02/kubuntu-and-hidpi-screen/](https://www.girialam.com/2016/02/kubuntu-and-hidpi-screen/):

> Finding the accurate DPI value is essential to find the accurate scaling value for the screen.First of all, we need to grep the connected screen: xdpyinfo | grep -B2 resolution.On my laptop, the output is:[INDENT] dimensions: 3200x1800 pixels (302x169 millimeters)
[/INDENT]
Since the value must be in inch, we then need to convert the value based on the output, so it is 302 ÷ 25.4 and then divide 3200 by 11.88. The result is 269. So this is it, the accurate DPI value for the 2015 HP Envy 13 is 269 DPI.By default, the DPI value in KDE is set to 96 DPI. To find the accurate display scaling value we need to divide the accurate DPI by 96, so it is 269 ÷ 96 which is 2.8.Now head to System Settings > Fonts > Force fonts DPI to set the DPI value and to System Settings > Display and Monitor > Display Configuration > Scale Display to scale the screen display, then re-login.After scaling the display the UI will looks rather odd where the icon seems too small, so we need to readjust the icon size, this must be done manually as KDE will not scale it automatically when non-integer value is set. Head to System Settings > Icons > Advanced and double everything in there.[[IMG]https://www.girialam.com/wp-content/uploads/2016/02/snapshot3-150x150.png[/IMG]]("https://www.girialam.com/2016/02/kubuntu-and-hidpi-screen/snapshot3/")
Screen Scaling[[IMG]https://www.girialam.com/wp-content/uploads/2016/02/snapshot6-150x150.png[/IMG]]("https://www.girialam.com/2016/02/kubuntu-and-hidpi-screen/snapshot6/")
Resizing Icons
Now, verify if the system is using the given DPI value with xdpyinfo | grep dots. Finally to make the changes survive system reboot, we need to create a file named 77set_dpi and enter xrandr --dpi 269x269 in /etc/X11/Xsession.d/[INDENT]$ nano /etc/X11/Xsession.d/77set_dpixrandr --dpi 269x269[/INDENT]
Other best practice is to create .Xresources in /home/USER/, so that non DE&#8217;s applications will also use the given DPI value as well as other display configuration such as anti-aliasing and font hinting. My .Xresources parameter is as follows:[INDENT]Xft.dpi: 269
Xft.autohint: 0
Xft.lcdfilter: lcddefault
Xft.hintstyle: hintslight
Xft.hinting: 1
Xft.antialias: 1
Xft.rgba: rgb[/INDENT]
[INDENT]
[/INDENT]

---

### Post by vasa1 on 2017-01-24
Please use quote tags to make it clear what is sourced from the site you've linked to. Thanks.

---

### Post by july8six on 2017-01-25
I updated my post.

---

