---
title: "Has anyone got an overhead scanner working with Ubuntu?"
date: 2022-01-08
forum: Hardware
---

### Post by Bernd_Wechner on 2022-01-08
There are a number of cool and affordable overhead scanners on the market now for some while already like:

[LIST]
[*][Fujitsu ScanSnap SV600]("https://www.fujitsu.com/au/products/computing/peripheral/scanners/soho/sv600/") 
[*][CZUR scanners]("https://czur.com/") 
[*][piQx scanners]("https://www.piqximaging.com/") 
[*][IRIScan Desk]("https://www.irislink.com/EN-AU/c1956/IRIScan-Desk--5-Pro---Document-camera.aspx") 
[*][Eloam scanners]("https://en.eloam.cn/BS2000P.html") 
[*][ICODIS scanners]("https://www.projecticodis.com/") 
[*][Viisan scanners]("https://www.viisan.com/en/product/Book-Scanners.html") 
[*][Unbranded overheads (with an SDK)]("https://www.ebay.com.au/itm/174834064991?epid=820125197&hash=item28b4ec1e5f:g:5GgAAOSwz7NfNAy3") (go China go!) 
[/LIST]
 I could go on. There seem to be a largish number of more obscure brands too. 

Alas the marketing is mostly atrociously unclear about support needs.  Some like the piQx are nice enough to say they don't support Linux, some actually mention you need Windows or Windows or mac, many don't say anything.

I have even found some dated and incomplete tests and mentions:

[LIST]
[*][http://www.johnwillis.com/2016/04/czur-scannerscanning-with-linux.html](http://www.johnwillis.com/2016/04/czur-scannerscanning-with-linux.html) 
[*][https://gitlab.com/sane-project/backends/-/issues/89](https://gitlab.com/sane-project/backends/-/issues/89)
[*][http://natecraun.net/articles/linux-guide-to-book-scanning.html](http://natecraun.net/articles/linux-guide-to-book-scanning.html) 
[/LIST]
But nothing overwhelmingly comforting that I'd base even a $200 investment on.

There are three distinct solution possibilities here:

[LIST=1]
[*]A scanner that does not require a PC connection, can scan a thumb drive or over WiFi to any server via FTP or other protocols or send images to an email address etc, all solutions I've known flatbed scanners to provide.
[LIST]
[*]Possibly with FOSS software on Ubuntu can can do page curvature correction and straightening etc like many of these scanners offer out of the box (with the oft unstated presumption you use Windows). 
[/LIST]
  
[*]A scanner that has Linux software support (seems a low priority with producers, and one of our best friends, Brother, doesn't seem to make an overhead scanner) 
[*]A scanner that has been tested on a Windows VM (VirtualBox or other). MS of course provide developer images of Windows and I use those for other spot needs - in my case I have one set up just for Microsoft ICE as alas nothing FOSS, not even  Hugin holds a candle to CIE for scan stitching - it's hard even to find ICE anymore as Microsoft discontinued it rather that FOSS it the blighters) 
[/LIST]
 I wonder has anyone here any experience to report. It seems I could justify a doctoral dissertation researching all the overhead scanner options and their various support and functioning with different OSs and Virtual OSs etc ;-). I've spent two nights on it already and feel fundamentally not much the wiser or better positioned to buy one.

But I do have Ubuntu laptops and desktops and nothing Windows bar VMs or Mac, and would want an overhead scanner that works in for me. 

It would be a positively awesome thing if we could collate experience, or coordinate tests if anyone happens to have one and can report etc.

---

### Post by TheFu on 2022-01-09
Most people are probably happy using their phones for quick scanning.
I've seen some people with DIY high quality cameras mounted over a light-box used to "scan" (really photograph) pages with 20+ mpixel images.  Youtube is full of people doing that, usually for images or when the content to be scanned will not lay flat.  A piece of glass to flatten/hold down some content helps greatly.

I've used Linux to run my Brother scanner for years.  It has a sheet feed, which I wanted to make scanning multiple pages easier. It is supported by **sane**.  **gscan2pdf** is my tool of choice - it has a GUI - which will shock long-time posters who know me. LOL.

It has been years since I set it up. Vaguely remember using the brother drivers installer - which are a little odd, but work.
I had an Epson before, but it didn't work.  Also had an Epson inkjet that didn't work a few decades ago, so I stopped buying their stuff.  I let my money support Linux-compatible hardware.

I also have a USB slide/negative scanner. This is plug-n-play with Linux, but it isn't exactly high-quality. Perhaps 300dpi and the light source provided isn't even.

Is researching scanners really worth a a dissertation?

I suppose the purpose for scanning and the source material would matter greatly.  Is this a 8x11 or 4ft x 4ft scanner?

OT: Plain FTP shouldn't be used - ever - since 2002. It is a security failure, unless the intent is to make something available to the entire world.  Modern browsers have removed plain FTP support (rightly).

---

### Post by Bernd_Wechner on 2022-01-13
I have no desire for a quick scan, I use my phone for that too. I'm looking at a mountain of material that needs scanning. Not quick ;-).

Brother scanners work just fine I have two of them, flatbed A4 alas and I have a lot of larger form material and want also faster than these flatbed scanners do if I can get it.

FTP is not a security issue at all when scanning if you use it as I do, internally on the LAN. I don't expose FTP ports to the WAN. But that's by the by, I use FTP on my favoured Brother MFC (Scanner) mainly because one day, out of the blue the other option it supports stopped working. 

Does researching scanners need a dissertation, not but it would rock if people collected their experience with them. Yes I can build one:

[https://diybookscanner.org/forum/viewtopic.php?f=26&t=3663](https://diybookscanner.org/forum/viewtopic.php?f=26&t=3663)

But since that DIY stuff became popular like it or not a lot of overhead cheap camera based scanners are on the market as outlined. And they are not expensive and promise to work well. To wit it would rock if, like flatbed scanners before them, we started collecting information on what devices worked with Ubuntu and which didn't and so on and sharing experiences.

To wit, sure, it may be a smaller market I'm appealing to, folk like me who have project that are beyond quick phone scans (which are great but not quick, as in to get a good one I have a great app that lets me move my phone around to four spots while it's watching and then creates a great composite scan. But I'd be after snap, flick, snap, flick, snap, flick on mixed format stuff that my paper feeder is useless on and A4 flatbed too small for.

Still, thank you very kindly for noticing and sharing your thoughts, it is appreciated, I am in no way dismissive of , and worry it may appear that way simply because you rightly suggest a few things that are already considered and I guess not what I'm after - the problem on the table here being, to get some traction on overhead scanners that work with Linux. 

There's one guy many years ago now had a CZUR working and wrote about (link in my post) but it's dated and and not very complete, but surely others have tried. Anyhow, hoping some folk in that camp finds this thread some time and have something to share. The DIY thread may have more traction as I'm more likely to find a Windows user there who migth out of interest install Linux and see etc. Fingers crossed.

There's a chance I may just take a punt and invest a couple hundred into being the guinea pig here in time and report back on one experience.

---

### Post by hilbricht on 2022-05-14
> **Bernd_Wechner said:**
> There are a number of cool and affordable overhead scanners on the market now for some while already like:

[LIST] 
[*][CZUR scanners]("https://czur.com/")
[/LIST]


[LIST]
[*][http://www.johnwillis.com/2016/04/czur-scannerscanning-with-linux.html](http://www.johnwillis.com/2016/04/czur-scannerscanning-with-linux.html)
[/LIST]
 
There are three distinct solution possibilities here:

[LIST=1]
[*]A scanner that does not require a PC connection 
[*]A scanner that has Linux software support 
[*]A scanner that has been tested on a Windows VM (VirtualBox or other) 
[/LIST]
 I wonder has anyone here any experience to report.

Regarding a CZUR Aura Mate Pro - all three possibilities work:
- You can operate the scanner with a smartphone app and then send the image to your Linux PC via KDEconnect or similar
- The scanner is detected in Linux for what it is - a camera. The kernel (here 5.13) detects it as UVC device and it can be used in various Linux applications, e. g. guvcview, OBS studio, Webcamoid, VLC, Vuescan or qstopmotion. Applications such as Gimp or Image Magick can then be used to manipulate the images, scantailor is quite useful too and has a function to flatten curved pages. A Linux workflow is possible, but it is not as straightforward as with the Windows-only software delivered by CZUR.
- I can confirm that the device is working on a Virtualbox VM with Windows 10 with the CZUR windows software including the foot pedal and adjusting the lamp.

I am quite happy with the device, because I can scan up to 39 cm x 29 cm in 300 dpi resolution, I can scan books and exercise books very conveniently, I can use the camera for stopmotion and other images, it saves a lot of space compared to one of those big MFC boxes (especially if you need scans larger than DinA4 / letter size) and it is easier to feed (unless you have an automatic document feeder), and  I can use it just as a lamp, too. Considering these advantages, I think the money was a good investment.
Cheers

---

### Post by Bernd_Wechner on 2022-05-14
> **hilbricht said:**
> Regarding a CZUR Aura Mate Pro - all three possibilities work:
- You can operate the scanner with a smartphone app and then send the image to your Linux PC via KDEconnect or similar
- The scanner is detected in Linux for what it is - a camera. The kernel (here 5.13) detects it as UVC device and it can be used in various Linux applications, e. g. guvcview, OBS studio, Webcamoid, VLC, Vuescan or qstopmotion. Applications such as Gimp or Image Magick can then be used to manipulate the images, scantailor is quite useful too and has a function to flatten curved pages. A Linux workflow is possible, but it is not as straightforward as with the Windows-only software delivered by CZUR.
- I can confirm that the device is working on a Virtualbox VM with Windows 10 with the CZUR windows software including the foot pedal and adjusting the lamp.

I am quite happy with the device, because I can scan up to 39 cm x 29 cm in 300 dpi resolution, I can scan books and exercise books very conveniently, I can use the camera for stopmotion and other images, it saves a lot of space compared to one of those big MFC boxes (especially if you need scans larger than DinA4 / letter size) and it is easier to feed (unless you have an automatic document feeder), and  I can use it just as a lamp, too. Considering these advantages, I think the money was a good investment.
Cheers

Thanks enormously for let me know all that. Looks I'll get me a CZUR then. I was hoping to hear from someone like you has used it with Linux and/or a Windows VM and phone app etc. 

Scantailor alas is no longer maintained, and looks like you have to build it from source of Linux alas. We ahll see. I'll go a CZUR shopping.

---

### Post by tomtom8003 on 2023-04-19
Have the same problem with an CZUR Shine pro. Starting a Windows VM works but is cumbersome. You can pause the VM with RightCTRL+P, but still using memory.

So, I ended up firing this command:
[FONT=courier new]fswebcam -r 4160x3120 --jpeg 100 -D 1 -S 10 fswebcam-in.jpg && convert fswebcam-in.jpg fswebcam-in.ppm && unpaper -vvv -layout single -dn left  -dv 5 --overwrite -S a4 --sheet-background white --no-grayfilter -b 0.5 fswebcam-in.ppm fswebcam-out.ppm && convert -trim -brightness-contrast 20x15 fswebcam-out.ppm scan_czur_`date +%Y%m%d`.jpg[/FONT]

It uses "fswebcam" ([FONT=courier new]sudo apt-get install fswebcam[/FONT]) to get the picture from CZUR, after a delay -D of one second and skipping -S 10 frames. Then you need to convert to PPM to let the scanned A4 on black CZUR rug be rotated and centred by "unpaper" ([FONT=courier new]sudo apt install unpaper[/FONT]). Then re-trimed, adjusted and converted to JPG. This works for me for fast scanning A4. For everything else, I still need the VM.

I'm disappointed by CZUR, because there is a Linux driver for the ET24, so it shouldn't be so hard to make version for other CZUR products.
BTW, you don't need a CZUR, just fix a good webcam over a black rug.

---

