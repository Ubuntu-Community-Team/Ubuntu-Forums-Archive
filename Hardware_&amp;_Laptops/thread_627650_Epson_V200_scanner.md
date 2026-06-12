---
title: "Epson V200 scanner"
date: 2007-11-30
forum: Hardware &amp; Laptops
---

### Post by robc02 on 2007-11-30
Has anyone got one of these scanners working on Gutsy? I am thinking of buying one but would like a bit of reassurance first!

---

### Post by mcouture on 2007-12-03
I'm interested too.  I have 100's of old slides from my grandparent's estate I need to scan to digital...

---

### Post by robc02 on 2007-12-03
If you want high quality slide scans this may not be what you want. This website has some good information about scanning:
[http://www.scantips.com/]("http://www.scantips.com/")

He likens the film attachments that come with most flatbed scanners to the free toys that come with breakfast cereals - if they work then OK but don't expect much!

Anyway, from what I gather the linux drivers don't usually support the finer features of most scanners - I presume that film attachments come into this category. There is a program called Vuescan that is meant to support a whole range of scanners including specialist film scanners. It is cross platform so should work on Ubuntu. Allegedly, it gives better results on Windows that the manufacturers' own drivers. Ubfortunateley you have to pay for it. For more info:
[http://www.hamrick.com/]("http://www.hamrick.com/")

I wonder if any Ubuntu users have tried it?

Personally, all I am looking for at this stage is to get some decent quality document and photo scans and the V200 looks as though it will be a bit better than the cheapest scanners (eg Canon Lide 25). Can anyone comment on this?

---

### Post by Josko on 2007-12-07
I have it and I installed drivers like described here: [http://ubuntuguide.org/wiki/Dapper#Install_the_correct_drivers:_Epson_Perfection_V200_Photo_example](http://ubuntuguide.org/wiki/Dapper#Install_the_correct_drivers:_Epson_Perfection_V200_Photo_example)
And it's fully working :) (even 35mm negative scanning) but only 3200dpi.
btw I have Gusty.
//Edit: 3200dpi in iscan only, in XSane is full 4800dpi.

---

### Post by robc02 on 2007-12-07
That's exactly what I was hoping for - thanks. I'll put one on my Christmas list!

Despite comments about built in film scanners being like breakfast cereal toys, I will be pretty pleased to have one that does work, even if it is a bit limited.

:)

---

### Post by Josko on 2007-12-07
When you'll install it notice that you have to add epkowa into /etc/sane.d/dll.conf wich is not written in link that I posted.

---

### Post by robc02 on 2007-12-14
I've just got my V200 and followed the installation instructions on the link you gave. I have just done a successful test scan and it works OK. Thanks for your help.

I didn't have to add "epkowa" to my dll.conf file, and it is not there already. Any idea why this should be? What does the dll.conf file do?

---

### Post by failte200 on 2007-12-28
> **robc02 said:**
> 
I didn't have to add "epkowa" to my dll.conf file, and it is not there already

I just got this scanner for myself for xmas, and on my Ubuntu 7.10 - with all the updates as of Christmas '07 - SANE still wouldn't detect the scanner until I added that line to the dll conf file just as he said.

Works fine now, though.  I thought Epson was supposed to be Linux-friendly...

---

### Post by robc02 on 2007-12-28
Isn't it strange? I did not add "epkowa" to dll.conf and have been using the scanner without problems. Even the negative/slide scanner works OK with achoice of resolutions - 300, 2400, 4800 dpi.

 I would still  like to know what dll.conf does and what is the significance of the "epkowa" line.

---

### Post by old_salt on 2008-01-05
Unfortunately once again nothing for us 64bit users. Anyone have any suggestions ?

---

### Post by eeried on 2008-02-05
> **robc02 said:**
> Isn't it strange? I did not add "epkowa" to dll.conf and have been using the scanner without problems. Even the negative/slide scanner works OK with achoice of resolutions - 300, 2400, 4800 dpi.

 I would still  like to know what dll.conf does and what is the significance of the "epkowa" line.

I didn't have to add it either because installing the deb packages did the trick.

The diffrence is in the two drivers: epkowa is the driver to use. You can comment out the "epson" line in the dll.conf

To install I used the French ubuntu doc that's quite clear.

I have some problems however with V200, and the v200 online manual isn't always very helpul:

- I can't switch off the scanner after using it a while. I push on the right button for at least 3 seconds and the light flashes and the scanner is still on.

If I unplug the usb cord from the scanner end, I then can swiccht it off but this may not be the right way at all.

- I need some help with scanning slides and negative films. robc says it's okay.

I think I've followed all the steps as seen on the manual. If I understand right the idea is to put the slide with the right side facing the scanner glass (of course I use the holder).

Now what can you you see when you do a scanning preview. I can see the holder and the slides or film inside. I expected to see the slides not the whole holder...

Now what settings do you use? i've tried dias, Kodak negative and so on and I get weird colours. 

I expected to be able to scan several dias (the images not their frames :confused:

Your help will be much appreciated!

---

### Post by eeried on 2008-02-05
I've moved a step forward by reading the Vuescan doc.

I've set one setting to transparency instead of flat bed, and another to Dia.

I can see the slides only. But the result is rather horrible: I tried with 300dpi and 2400dpi (which took a long time on a celeron core 420 and 512Mo RAM).

The pictures are made of dots like some impressionistic paintings,a nd the colours are totally wrong with a blue hue on one of the slides.

- The preview is hardly that at all: I can see a strip but I don't know how it'll turn out; so you need to scan before changing anything. Is this the case with your Xsane (I've got Gusty).

With some ordinary pictures the preview is less good than the scanned picture.

---

### Post by robc02 on 2008-02-05
I can't switch mine off either!

I was going to ask if you had selected "Transparency Unit".

Where is the "dia" setting?

I have only tried black and white negatives, but I got respectable previews. I tried scanning at various resolutions - 300dpi was probably good enough for email/ebay purposes and 4800 dpi seemed pretty good but took quite a long time. To scan a single negative I selected it from the Preview image.

I tried several different film type settings and found quite a difference between them - mainly in contrast from what I remember. I was using Ilford Pan F negatives and found the "Standard Negative" setting to be about the best. I reckon it will take quite a bit of playing about with some of the other settings to get a really good result, especially in colour. You will probably need different settings for different film types and, maybe, for shots taken in different lighting conditions. 

I should add that I have only done a few experiments so far, and they were late at night when my interest was waning! I will be interested to hear how you get on and I will have another go myself when I get a bit of time.

---

### Post by Rhubarb on 2008-02-05
I've been doing A LOT of fiddling with my epson v200 scanner in gutsy over the last few days.
I've been very successful with regards to positive slide scanning and experimentation with it.

So far my results have been excellent, colours come out fine, everything has been quite good.
I've also been doing a lot of research into what picture format is best for archiving scanned in slides (png is very good as it's lossless).

Unfortunately I can't reply too much now, as it's very late, and I'm very tired, so I don't want to give out any advice now.

I'll post back here tomorrow when I'm awake!

---

### Post by robc02 on 2008-02-05
Eeried, I've just had a go at scanning a slide -  a shot taken in natural daylight using Fujichrome 200.

First of all, the preview was sufficiently detailed for me to see that the image was basically OK. I then used the cursors to select the slide, and tried the following scans:

1. File type - jpeg, resolution - 300dpi, full colour range, default settings for gamma, brightness and contrast. Scanning was pretty quick. File size 13.1k

2. As 1 but file type - png. File size 158.8k

3. As 2 but resolution - 2400dpi. File size 6.3Meg

4. As 3 but click on the icon "autoadjust gamma, brightness and contrast". File size 6.7Meg

Scans 1 and 2 had similar image quality but the colours seemed very slightly brighter on the jpeg  image. As you might expect the quality was not very good, especially when zoomed in, but was OK for assessing the image for further scanning, or other less critical viewing.

Scan  3 was considerably more detailed, but took quite a lot longer to scan. In each of the scans so far the colours were not bad, but perhaps the day looked duller than it actually was.

Scan 4 had better brightness than any of the previous scans, so the autoadjust was definitely worth using in this case.

Basically, I got pretty reasonable results in just a few minutes and without any major fiddling. In view of the comments on [http://www.scantips.com/]("http://www.scantips.com/") I am pretty pleased with that.

I will be interested in Rhubarb's next post.

Has anyone tried the Vuescan software?

---

### Post by Rhubarb on 2008-02-06
This is in regards to scanning Kodachrome Transparencies (positive 35mm slides) from 1969 taken with a terribly cheap camera.

I've found xsane to be the best scanning application in ubuntu so far.
I couldn't get kooka working, iscan (epson scanning software) crops the slides, and does not provide many options (such as batch scanning).
Even the windows software that comes with the v200 scanner is poor (it auto-crops your slides which is a huge problem if you have some dark slides).

My task is to scan in 1200+ slides for archiving.  Hence I've been doing a lot of tinkering and research into this.

**PNG info:-**
I've found that the png format is best, as it is lossless, and supports meta tags (so you can put comments in them).
PNG also supports 48bit colour, but unfortunately there's poor support in most applications for 48bit colour PNGs today.

**PNG compression:-**
Depending on your CPU speed and hard drive space, use PNG compression = 1 (I've found this gives you a nice balance between file size and time taken to save the file after scanning, this is with a 1.7GHz core duo processor).
Use compression = 0 if you have a slower CPU (this will create a much larger file size).
It is possible to re-compress your PNGs later on (there is no loss in detail or quality of the photo).
```
pngcrush foo.png
```

**PNG metadata (comments):-**
I'm still checking up with the best way to add comments to PNGs, so far GIMP is best (press Alt + Enter when in a photo).  Never use F-Spot to comment your photos for archival purposes, it's simply not designed to do it.
There are several command line utilities to view metadata info inside PNGs:
```
exiv2 foo.png
pngmeta foo.png
identify -verbose foo.png    #you need the imagemagick package to do this
```

**DPI:-**
You need to play around with dpi settings to get the best quality scans from your slides.
I've found that 2400dpi is best, as 4800dpi brings no more detail at all.

**Scan source:-**
Make sure it's on Trasparency Unit (this really goes without saying)

**Scan mode:-**
Should be Color (I'd prefer if it was UK english - colour, but I won't whinge about this too much)

**Source medium type:-**
Full color range,  I don't think there's much difference between slide and full color range.

**Bit Depth:-**
Should be 8, as 16bit support is poor in many applications.

**Gamma correction:-**
1.8 seems to give the best results for me.

**Scanning it in:-**
Acquire a Preview, then draw a little box around the slide you wish to scan in in the preview window.
Then in the main xsane window, there's a button down the bottom, "Autoadjust gamma, brightness and contrast <Ctrl-e>", press that to get the best results.
If you want to store these settings, press the M button at the right bottom of the main xscan window.
Now hit the scan button and sit back :)

**Touching up the photos:-**
To enhance the photos after scanning, you can use GIMP.
In the Colours menu, you can either do it manually, or try out some of the auto options.
Colours --> Auto
Then try out the Equalise, White balance, and Normalise options there.

**Other stuff that I'm currently investigating:-**
*Better ways to add metadata comments inside PNG images (there's a few apps that might be able to do this)
*Using mogrify or other tool inside imagemagick to create some black below the slide, then using another imagemagick tool to write some text in here, so text is preserved in the picture, not as metadata.
*The batch scanning seems very good in xsane, but I'm not sure yet if it uses the same gamma / brightness / contrast profile on all of the scans in the batch.  I might be able to do this by using the command line version of xsane.
*I might be able to scan in the whole strip in xsane, then use imagemagick to crop out the individual slides, then preform some auto gamma contrast brightness settings from a bash script.

Hopefully I haven't missed out on anything here, I know quite a lot now, and there's still a bit more for me to wade through.
Let me know if there's anything else you'd like to know.

Edit:  I can't turn off the scanner either.  The only way I found is to disconnect it, then turn it off.  Or just turn off your scanner after you've shut down your PC.
After about 10 minutes since scanning, the scanner goes into stand-by mode anyway, so the transparency light in the lid turns off.
I wouldn't worry about leaving the scanner on while your PC is on.

---

### Post by haiku88 on 2008-02-06
thanks very much, this worked for me too using an Epson V200 w/ Gutsy...

---

### Post by eeried on 2008-02-08
Many thanks for all the info, robc02 and Rhubarb!

What I did wrong was to set "dia" instead of leaving the default "color" setting --  robc02, the dia and other settings are below the "color" settings. 

The preview is fine, now: I can see miniatures of each slides in a row on the left-hand edge of the preview window with acceptable colours.

First try: 300 DPI, gamma setting was automatically set at 1.2. I simply viewed the output as out.pnm (default setting). It's okay. the original slide was was a bit dark : slate-grey masses of clouds, and the output was very similar to the slide. 

My second try was allright too: this time I set Xsane to save the picture as png -- yes PNG is good though many people ignores this excellent format. TIFF would be great too if your picture get printed in a book.

If you need to edit your scanned picture, it'd be best to scan from GIMP, save it in GIMP format (XCF) and only save a copy as PNG once your editing is over and you're really satisfied with your picture.

GIMP doesn't support 16-bits but surely you can open a picture that was scanned in 16-bit depth. Still have you noticed a difference between the 8 and 16-bit depth?

- What's weird in the outputs is the pictures don't look natural, there aren't sharp and viviid as the slides, and they look as if they had as if they had been modified with an oil-painting effect, sort of. It's difficult to describe. I'll post a picture on our website in a moment.

- I find the options in the preview window rather confusing. i'll try to find some doc about them.

- Finally how do you go about scanning 4 slides in a row? Do you use the batch option or do you scan the 4 slides in a row and cut out the black bits later on?

I'm glad nobody here can switch off the scanner because that means there's nothing wrong with ours! i suppose the driver has a bug though the switch off works inside a minute or two after switching it on. But this is hardly useful!

Cheers,

---

### Post by eeried on 2008-02-08
picture posted: [http://libre-zele.info/?q=node/210](http://libre-zele.info/?q=node/210)

---

### Post by Rhubarb on 2008-02-08
> My second try was allright too: this time I set Xsane to save the picture as png -- yes PNG is good though many people ignores this excellent format. TIFF would be great too if your picture get printed in a book.
Yes indeed TIFF is a lossless format, and it is still quite good.  It's just that it's a bit old, and doesn't compress as nicely as PNG does (and I'm not sure if TIFF supports meta information).

> If you need to edit your scanned picture, it'd be best to scan from GIMP, save it in GIMP format (XCF) and only save a copy as PNG once your editing is over and you're really satisfied with your picture.
Yes, the beauty of XCF is that it can save layers amongst other things.
But I don't think GIMP is the best to use when you need to scan in 1200+ slides en masse.

> GIMP doesn't support 16-bits but surely you can open a picture that was scanned in 16-bit depth. Still have you noticed a difference between the 8 and 16-bit depth?
To be honest, I haven't found many applications in Linux that supports 16-bit per channel colour depth.
The closest application that seems to support it is [http://www.cinepaint.org/](http://www.cinepaint.org/) , I haven't tried this application as it doesn't seem suitable to my usage needs.
I have noticed that viewing a 16-bit depth scan in GIMP / Eye of Gnome / gThumb results in a very grainy image, that looks like it's composed of very few colours.

> - Finally how do you go about scanning 4 slides in a row? Do you use the batch option or do you scan the 4 slides in a row and cut out the black bits later on?
I haven't decided on this yet, as I'm not sure if the auto correct gamma / brightness / contrast button should be used in all slides, or if the same setting can nicely apply to all the 4 slides in the scanner.
Unfortunately I can't test this out as I don't have access to the scanner for the next few days.
I'll try it out both ways, to see which is faster.
The batch scanning is useful, but may not be as fast as scanning the whole strip in, then using imagemagick to automatically crop the 4 slides from the strip.
I'll get back to you regarding this soon.

In a month or so I'll attempt to get the scanner to work with my 64bit Ubuntu install on my other computer.

---

### Post by eeried on 2008-02-10
Many thanks for your reply Rhubarb!

I totally agree that PNG is great, and it's an open format, which is a great thing! Strangely enough ORC software like tesseract seem to like TIF better.

You're right about 16-bits depth: when I use it to scan a slide I get a very grainy image. So thank you for pointing out the 16-bits depth incompatibility hitch. Let's stick to 8-bits depth.

This is a good idea to use imagemagick to crop the 4 slides from the strip! I'll pore over the doc to see how it can be done.

Another question: in Xsane do you have other resolution choices than 300dpi, 2400dpi, 4800dpi?

BTW, I've been experimenting with OCR, and I installed tesseract and gscan2pdf from  DEB packages and a script so as to get the newest versions of the software, and it's rather fun. There's some good documentation on the  Ubuntu-fr wiki, but there doesn't seem to be anything in the Ubuntu-en user doc:  
[http://ubuntuforums.org/showthread.php?p=4304463](http://ubuntuforums.org/showthread.php?p=4304463)


To get back to the main topic of this thread, yes Epson V-200 seems to be a good deal as it is  a good versatile scanner at a reasonable price. The only hitch is that it can't be switched off after a while, but I haven't tried switching it off after the computer is off, and before switching off the plug itself.

---

### Post by 2CV67 on 2008-02-21
Thanks for this thread!

I had just come to the conclusion that Ubuntu could not run any of the current, reasonably-priced stand-alone scanners with mounted-slide capability (Canon CS4400F, HP G4010/4050, Epson V200/V350 etc).

In spite of the problems near the beginning of the thread, can I now conclude that the V200 will work adequately in Ubuntu 7.10?

Is anybody going to update the "Supported Hardware" pages?
[https://wiki.ubuntu.com/HardwareSupportComponentsScannersEpson](https://wiki.ubuntu.com/HardwareSupportComponentsScannersEpson)
These pages really present a bleak picture for anybody looking to buy a new scanner, or wondering whether to switch to Ubuntu!

Do any of the other current slide-capable scanners work in Ubuntu?

Thanks again.

---

### Post by eeried on 2008-02-21
> In spite of the problems near the beginning of the thread, can I now conclude that the V200 will work adequately in Ubuntu 7.10?

Have you read to the end? :)
eeried wrote:
> To get back to the main topic of this thread, yes Epson V-200 seems to be a good deal as it is a good versatile scanner at a reasonable price. The only hitch is that it can't be switched off after a while, but I haven't tried switching it off after the computer is off, and before switching off the plug itself.

> Is anybody going to update the "Supported Hardware" pages?

Thanks for reminding us! Just don't touch the wiki which is obsolete, I think you need to update the page on this web site: [https://help.ubuntu.com/community/UserDocumentation](https://help.ubuntu.com/community/UserDocumentation)

And there's another place for hardware on Ubuntu but I can't remember the URL. :confused:

cheers

---

### Post by Rhubarb on 2008-02-24
In XSane 300, 2400, and 4800dpi are the only resolutions I've got.
iscan allows me to have 50, 72, 96, 150, 200, 240, 266, 300, 350, 360, 400, 600, 720, 800, 1200, 1600, 2400, 3200dpi
But don't use iscan, as it doesn't scan in the whole slide (it won't let you scan in about 10% of the right hand side of the slide).
Also it'd be best to scan in only a few resolutions, as scanners can't really have a true arbitary dpi setting, so use 4800, 2400, 1200, 600, 300, 150, or 75dpi if you have the choice.

I have yet to try and get the V200 scanner working in 64bit Ubuntu 7.10 - I'll probably try sometime in the next few months.  With any luck by then Epson would have released 64bit drivers for it / sane fully supports it in the open source drivers by then.

I have not tried using imagemagick to crop and balance the slides yet, as it's quite simple to use the batch scanner in XSane (but remember to autoadjust the gamma / brightness / contrast for each slide, and scan in only one slide at a time).
The batch scanner is great as it just stores the offsets for each slide, so you don't need to drag a selection box over each slide.

As always, I'll regularly check this thread and post back anything new that I find.  :)

---

### Post by eeried on 2008-02-25
In fact, 300DPI is quite convenient.

As a matter of fact I'm not too sure how to use the batch feature. I've successfully scanned two selections in the same document, by saving each after the other (batch icon in the preview window).

I thought you could save previews of several documents, and then scan them all in a row. But I didn't succeed. How do you go about it if it is at all possible?

---

### Post by Rhubarb on 2008-02-25
In the main XSane window, click on Windows, then the batch window.
This will bring up the batch editor window thing.

I'm not at my scanning PC right now, so I can't say exactly what to do.
But once the batch window is up, just play around with it.
It's extremely good at scanning in batches of 4 slides.  Though remember the auto-correct gamma / brightness / contrast only works on the selected batch entry, so you really should scan in one slide at a time rather than the whole batch.

The batch window enables you to select pre-defined areas in the preview window, so you don't need to crop out the area you want to scan in all the time.

I'm very sleepy at the moment, so I apologise for anything that doesn't make that much sense here.

---

### Post by 1inxs on 2008-03-31
Hey All,
  I've been back and forth between Ubuntu and Fedora 8. Linux users seem to be experienced in many flavors. Is there a chance anyone here could help me get my Epson V200 working in Fedora? There is no success post in Fedora Forums, which is why I'm posting here.
Thanks

---

### Post by Rhubarb on 2008-04-03
I'd expect that Fedora 8 would be easier to get going, as there'd be no need to convert the rpm packages to deb ones.

I'm rather busy at the moment, so I don't have time to test fedora 8 and the V200 scanner for myself.
The most important thing that I can think of, is to make sure you're running 32bit Fedora (and not 64bit).

With any luck in a few weeks I'll have some time to test out Fedora and the V200 myself.  (I've yet to try getting the V200 working in 64bit Ubuntu).

---

### Post by 1inxs on 2008-04-06
Rhubarb,
Thanks for your help. I've never been impressed with the 64Bit, so I just stay with 32Bit.  I'll keep following this post and searching the web to get my Epson V200 scanner working.

---

### Post by 1inxs on 2008-04-10
A few of you have posted that pressing the power button does not power the scanner off. Do the other three (3) buttons work as designed? Thanks

---

### Post by Rhubarb on 2008-04-10
None of the buttons on the V200 actually do anything at all.
The power button will turn on the V200, but to turn it off you have to power down your PC / disconnect USB from the V200, then the power button will turn it off.

But, as XSane can email / print / fax / save to file / OCR, there's no point in having buttons on the scanner anyway, as all the functionality can be accessed from within XSane.

In a few weeks I'll try out the V200 scanner in Hardy Heron (Ubuntu 8.04).
Hopefully then I'll have time to try and get this scanner working in 64bit.

Let me know if there's anything else you want to know about the V200 :)

---

### Post by 2CV67 on 2008-04-10
Excuse me for inserting some non-expert comments here…

I am dual-booting XP/Gutsy and had been looking for a slide-capable scanner to replace an old HP4470c.
Thanks to this thread, I decided to get an Epson V200.

I have not yet tried it in Ubuntu, but my experience in XP may throw some light on others’ comments in Ubuntu;
The results, even for slides & negatives, are adequate for my non-expert usage at 2400dpi or 3200dpi (oddly less good at 4800 & 9600 & 12800?). Certainly not like a breakfast-cereal toy!
The controls & interfaces & instructions are terribly clunky.
When the Epson Scan utility is open, none of the buttons on the scanner work. 
This means you cannot turn off the scanner or decide to print from the button without shutting the Epson Scan utility!
That sounds about like what Ubuntu users are finding.

---

### Post by Rhubarb on 2008-04-10
I had tried the V200 scanner in windows, and came to the a nasty conclusion:  It couldn't scan in slides that had large dark areas in it, it would crop the images without my consent to do so.
Also it was inefficient to use for scanning in mass amounts of slides (we're talking 1000's of slides here).

And yes, I agree the interface for the epson software in windows is clunky, and abstracts many options away from you, even in "expert" mode.

XSane in Ubuntu is really powerful, it's a bit ugly, but it's very funtional.
Also, given some time I could probably implement a simple python program custom made for my mass slide scanning needs.
Ubuntu is just very flexible, and isn't afraid to give me configurability / customisation when I want it.

Also as I discussed earlier in this thread, the scanner simply doesn't scan in 9600 or 12800dpi, it just uses software to create a bigger image.
I could be wrong, the servo motors on the scanner may provide for smaller increments, but the resolution of the optical pickup is just 4800dpi.

---

### Post by 1inxs on 2008-04-24
Well I got my scanner working in Fedora. Anyone interested can see how here [http://forums.fedoraforum.org/showthread.php?t=185282](http://forums.fedoraforum.org/showthread.php?t=185282)
A few years ago I had Gentoo up and running, although hardware issues prevented me from continued use. I really liked using Debian. Now with a few weeks of tinkering with Fedora, I'm not so hip on RPMs. I have Ubuntu 7.10 (Debian based) on my PC and think I may end up with Ubuntu from now onward. Thanks for the courteous posts here at Ubuntu forums. That makes the change over smooth. I'll be using posts from this thread to get my Epson V200 scanner running. Thanks All!

---

### Post by 1inxs on 2008-04-24
Any idea what I'm doing wrong? I'm switching to Ubuntu 7.10. Trying to install my Epson V200. I can't even do the alien conversion. I get

robert@robert-desktop:~$ sudo alien iscan-2.8.0-1.c2.i386.rpm
[sudo] password for robert:
File "iscan-2.8.0-1.c2.i386.rpm" not found.
robert@robert-desktop:~$
EDIT: I had to enter full extension robert@robert-desktop:~$ '/home/robert/Desktop/iscan-2.8.0-1.c2.i386.rpm
That got it going.

---

### Post by robc02 on 2008-04-27
I have just installed Hardy and can't get my scanner to work.

If you have been following this thread you will know it was working fine on Gutsy, but when I tried to install it on Hardy I found there was no /etc/udev/rules.d/45-libsane.rules file. I had already installed the iscan driver and plugin, but cannot tell teh system that the scanner exists (I presume thiat is what the 45-libsane-rules file does).

scanimage -L does not show the scanner, even with sudo. 
lsusb does show it.

Any help will be greatly appreciated.

---

### Post by LakeWind on 2008-04-28
> **robc02 said:**
> I have just installed Hardy and can't get my scanner to work.

If you have been following this thread you will know it was working fine on Gutsy, but when I tried to install it on Hardy I found there was no /etc/udev/rules.d/45-libsane.rules file. I had already installed the iscan driver and plugin, but cannot tell teh system that the scanner exists (I presume thiat is what the 45-libsane-rules file does).

scanimage -L does not show the scanner, even with sudo. 
lsusb does show it.

Any help will be greatly appreciated.


Same problem here. It seems to be a bug. You can follow it here:

[https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/180794](https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/180794)

There are several duplicate bugs reported on launchpad as well. I haven't tried any of the suggestions yet but will eventually when I have the time. If I manage to get it working, I'll post a how to. If you get it working first, kindly do the same.

Good luck!

---

### Post by robc02 on 2008-04-28
I have just looked at the bug report. It's a good job I installed Hardy on a new partition, keeping Gutsy "just in case".

I have tried sane-find-scanner and it sees my scanner - without sudo.

I am a bit busy at the moment but when I get chance I will do a bit more digging and report anything useful.

---

### Post by eeried on 2008-04-28
> File "iscan-2.8.0-1.c2.i386.rpm" not found

links, are you sure you ran the command from the dir where your downloaded RPM file is?

---

### Post by Rhubarb on 2008-04-28
> **eeried said:**
> links, are you sure you ran the command from the dir where your downloaded RPM file is?
eeried, 1inxs' V200 is working now if you read the edit that was made.

I do hope this bug will be fixed soon with Ubuntu 8.04 + V200 scanner.  Some time next week I'll attempt to get it working.  For the moment, I'll keep 7.10 just for scanning purposes.
As always, I'll post here if I find anything, and I'll keep an eye out here if someone else posts here with a solution.

---

### Post by robc02 on 2008-04-28
I've got my scanner working! I added the line "epkowa" to the /etc/sane.d/dll.conf file as suggested here:
[http://uellue.de/blog/single.php?date=1192278660]("http://uellue.de/blog/single.php?date=1192278660")

So, to summarise, for Ubuntu Hardy users the process is:

Download the driver RPMs "iscan" and "iscan-plugin".

Unpack them and use "alien" to convert to deb packages.

Install them using the "dpkg --install" command or by right clicking on the file and then clicking "Open with GDebi package installer"

Add the line "epkowa" to /etc/sane.d/dll.conf

Check that your scanner is seen using "scanimage -L"

You should now be ready to scan using xsane.

One cautionary note - I haven't yet thoroughly tested my scanner, but it has successfully acquired a preview so it should be OK.

---

### Post by LakeWind on 2008-04-28
> **robc02 said:**
> I've got my scanner working! I added the line "epkowa" to the /etc/sane.d/dll.conf file as suggested here:
[http://uellue.de/blog/single.php?date=1192278660]("http://uellue.de/blog/single.php?date=1192278660")

Awesome! Thanks for taking the time to post this. I'll give it a try.

Thanks Again!
:)

edit: Tried it and it works! Many Thanks!

---

### Post by herdivet on 2008-05-09
I have also followed the posts in this thread to get the V200 working in Hardy.  I notice it simply will not respond to the scanimage -L command, but since XSANE recognizes it, I don't care.  I wasted a bit of time trying to troubleshoot what I thought was a non-working system when I got no response from scanimage, so if you try that and it fails, don't give up.

I also did not have the 45-libsane.rules file on this Hardy install, but it was on another system that I had installed the beta version and 'updated' through to the Hardy release version.  I copied it over and then added epkowa and everything has been joy since then.

Thanks for all the great information on getting this up and running!

---

### Post by Josko on 2008-05-10
Now I installed Hardy 64bit and was angry that there is no 64bit driver for linux for this scanner but I found solution:
I installed 32bit chroot inside 64bit system [http://ubuntuforums.org/showthread.php?t=733595](http://ubuntuforums.org/showthread.php?t=733595) and installed drivers converted from rpm's to debs by alien as described here [http://ubuntuguide.org/wiki/Dapper#Install_the_correct_drivers:_Epson_Perfection_V200_Photo_example](http://ubuntuguide.org/wiki/Dapper#Install_the_correct_drivers:_Epson_Perfection_V200_Photo_example) 
and then added the line "epkowa" to /etc/sane.d/dll.conf and I can use sane or iscan without any problens in my 64bit system now..
and notice: 45-libsane.rules is not there but there is /etc/udev/libsane-extras.rules instead.

I run iscan or xsane from icon in panel with this command: schroot -p iscan or schroot -p xsane. Only problem is that it consume about 600MB of hard drive space :(

---

### Post by 2CV67 on 2008-05-19
Meanwhile, back at the beginning...

As a dummy trying to install my V200 (thanks again for this thread!) I would appreciate a little advice please.

I downloaded the RPMs, converted to debs (with a warning about skipping conversion of scripts and did I want to use --scripts. Should I have done?) and installed them with no conflict about libsane.

lsusb showed the scanner.
It was not in libsane rules so I added it as indicated & saved the file & restarted udev. (I don't understand any of this - just following instructions).
With the scanner switched on: "sane-find-scanner" finds it "found USB scanner (vendor=0x04b8 [EPSON], product=0x012e [EPSON Scanner]) at libusb:004:008"

But "scanimage -L" does not "No scanners were identified. If you were expecting something different, check that the scanner is plugged in, turned on and detected by the sane-find-scanner tool."
I tried that as root too - same result.

xsane does not see it either.

I see obscure hints about adding "epkowa" but don't understand what/how/whether I need to do that.

Thanks for any clarification!

---

### Post by Rhubarb on 2008-05-19
> **2CV67 said:**
> I see obscure hints about adding "epkowa" but don't understand what/how/whether I need to do that.
You really do have to add the epkowa line in to get your scanner working.

To do this, you need to:
```
sudo gedit /etc/sane.d/dll.conf
```
Then you need to add **epkowa** to the list somewhere in there (I usually insert a line past epjitsu and before epson just so it's in alphabetical order).  Save and exit.

Now you may restart you computer, and xsane should work nicely with your V200 scanner.

Aside, I found it a bit easier to install the V200 scanner in Ubuntu 8.04 as I didn't have to edit the 45-libsane.rules file.
Now hopefully this gets open sourced and released to the xsane devs so there's a better chance V200 scanners (well, Epson scanners in general, will just work on 32 and 64bit Linux.

---

### Post by 2CV67 on 2008-05-19
That did it! :D

Many thanks!

---

### Post by 2CV67 on 2008-05-19
I am still playing with my V200 in Gutsy and am very pleased with most of what I have seen so far.

Except that slides seem to be less sharp than when I did them on the same scanner in XP.
Is that just my imagination (don't think so) or have I missed some setting?

I used 2400dpi in both.
In XP I had used "Unsharp mask" and quite a bit of jpeg compression but the same slide in Ubuntu, even in tiff or png or pnm (all much bigger files) looks less sharp.

Can anybody confirm or deny?

Thanks!

---

### Post by Rhubarb on 2008-05-23
> **2CV67 said:**
> In XP I had used "Unsharp mask" and quite a bit of jpeg compression but the same slide in Ubuntu, even in tiff or png or pnm (all much bigger files) looks less sharp.

Of course scanned in photos in Ubuntu look less sharp, because there is no option in XSane to apply an unsharp mask to photos that are scanned in (as there is in XP).

The unsharped jpg image as scanned in XP actually contains far less original detail than a png image without an unsharp mask (even though as you say it looks less detailed) - as an unsharp mask gives you the illusion of detail at the expense of a little actual detail, and jpg as you may know is a lossy file format (unless it's in jpeg2000).

If you want to apply an unsharp mask to your photos in Ubuntu, this can be achieved by loading them up in GIMP and applying the unsharp mask:  Filters --> Enhance --> Unsharp Mask

If you want to apply the unsharp mask en masse, this can be achieved with a reasonably simple command in a terminal as well (I don't know it off hand, but if you do want to know it please ask me and I'll look into it).

If you prefer to save in jpg rather than png, this can be easily done too.

---

### Post by 2CV67 on 2008-05-23
Thanks for that reply!

After a few tests in XP, I can confirm that the better-focused appearance is entirely due to "unsharp mask" and not related to Ubuntu/XP.

I had not deliberately chosen "unsharp mask" (crazy name!) in XP.
It seems to be the default condition there.

Yes I realize that jpg is famously lossy and that unsharp mask is a distortion, so philosophically I should dislike both, but in fact, judging my ordinary family photos with my ordinary eyes, via screen or printer, even pushing zoom, I can't see very much difference between a 18Mo scan in lossless tiff and a 350K scan with mid-level jpg compression, both without unsharp mask.
A 450K scan with mid-level jpg compression and medium unsharp mask looks "better" than either, so represents a lot more visual bang for the file-size buck!

I will try unsharp mask in GIMP as you suggest.

It would certainly be interesting to be able to apply it directly, but please don't spend time on that just for me!
Of course, if other people would also benefit...

Wonder why Epson chose to use it as default in XP and left it out for Linux? (Are they watching this thread?)

Thanks again!

---

### Post by DidYouReadGuyDebord on 2008-05-27
Hello! Could you please tell me how noisy or silent this scanner is when scanning? I have a dead flat Canon scanner that was horribly noisy (loud high pitch) when scanning, and I am looking for a quieter replacement!
Thank you!

---

### Post by 2CV67 on 2008-05-28
I find it quite noisy with a variety of high-pitched, cheap-sounding whines & warbles.

Much noisier than my Canon iP4300 printer, for instance (which has an excellent "silent" mode).

I operate in a room where the family are often watching TV & they turn up the TV volume when I am scanning...

I hope other people can give a better direct comparison with other scanners.

---

### Post by DidYouReadGuyDebord on 2008-05-28
Thank you very much for your answer!
I will have to buy the quiet Canon 4400F (according to comments on Amazon), then, even if it is not supported in Linux. And I will have to use Windows for OCR! Well, in a way it is realistic since Tesseract is not quite on par with Omnipage and Abbyy yet.
My ears thank you again! ;)

P.S.: I wonder if I can use a scanner unsupported by Sane through qemu.

---

### Post by eeried on 2008-05-28
I don't mind the noise Epson V200 makes. I can't draw any comparison because it's the first scanner I've really used. I'm rather thrilled at what it does and so I'm more bothered by the noise of the CPU fan that never stops.

You can look at page 3 and see gscan2pdf may be better than Tesseract.

About the Canon scanner, here's what someone says on LDLC, a near equivalent of Newegg:
> S'il est vrai qu'on n'a rien à redire sur l'appareil lui-même, les pilotes sont, en revanche, indignes d'une firme comme Canon. Et malgré une expérience certaine dans le domaine informatique, je n'ai toujours pas compris le rôle respectif de Canoscan Toolbox et Photostudio, ni leur fonctionnement, peu intuitif.
Invraisemblable... 

So a good scanner but lame drivers from Canon (for Windows I suppose), but this comment is over a year old so it may be outdated.

---

### Post by robc02 on 2008-05-29
This is my second scanner, the first was a Mustek Scanmagic 1200 that could not be made to work in Linux. The Epson is perhaps a bit quiter and smoother sounding. Personally, I dont find the noise intrusive. I am just delighted to get something that performs as well as this, for this price, and can be made to work in Linux.

---

### Post by 2CV67 on 2008-05-31
I reinstalled my old HP Scanjet 4470c to confirm the noise comparison - in XP of course as it will not work in Ubuntu.

The HP has a lower noise level, but mainly it is lower-frequency noise so is less piercing/irritating/cheap.
I don't have experience with any other scanner recently.

Like robC02 I chose the Epson (rather than a Canon 4400F in my case) purely because it will work in Ubuntu and that is more important to me than the noise level.
Epson should be supported for aiding Linux, even if it is not exactly plug & play.

---

### Post by DidYouReadGuyDebord on 2008-06-01
Thank you all for your answers!
Basically my mind is with Epson, but my ears went to Canon. I bought the 4400F (I use it on another computer with Windows). It makes a little high pitch noise when scanning at 300 ppi, and then a little louder medium range noise when bringing back the moving part to the top of the scanner. These noises are neither too stressful nor too loud, I think because they are rather simple sounds, although the medium sound is more complex.
It is very acceptable, especially compared to my older Canon scanner. Now I will not resent scanning!

---

### Post by boddhisatva on 2008-06-02
I've followed all the steps and managed to get XSane started on Hardy with this scanner, but it only scans in Black and White (not even greyscale), although it says "grey" on the progress bar (There was some problem while installing xsane-extras). On the other hand, iscan seems to scan OK. Why, any idea? I know iscan is for Epson specifically, but other people didn't seem to have a problem with xsane...

---

### Post by boddhisatva on 2008-06-02
Also, there are only 3 resolutions available in xsane (300, 2400, 4800). There is a whole range in iscan, but the maximum is 3200... Is it possible to get 4800 in iscan?

---

### Post by boddhisatva on 2008-06-02
Sorry, my mistake with the B/W scanning in XSANE. The mode was set to "binary", I just didn't read that as meaning B/W :). I believe the 3 resolutions in xsane are the rule, if I want more I go to iscan, if I want 4800 I go back to xsane. Problem is Xsane won't scan photos at 2400 or 4800 (out of memory) at 1GB RAM, whereas Kooka or Iscan has no problems with that (except Iscan can't scan above 3200). Also, all the programs cut the edges off the scan area, so I can't put the images near the edges...

---

### Post by robc02 on 2008-06-02
I don't know how big your photos are, but, unless they are very small pictures, the image file sizes will be enormous - this probably explains your lack of memory messages. It is well worth taking the time to have a good look at this website:
[http://www.scantips.com/]("http://www.scantips.com/")

He goes through the whole business of resolutions etc. in some detail. I must confess that I haven't yet read it thoroughly, but the bits I have read have made me realise that more is not necessarily better.

These pages might be of particular interest:

[http://www.scantips.com/chap3c.html]("http://www.scantips.com/chap3c.html")
[http://www.scantips.com/basics1e.html]("http://www.scantips.com/basics1e.html")
[http://www.scantips.com/basics1d.html]("http://www.scantips.com/basics1d.html")

Hope this helps.

---

### Post by boddhisatva on 2008-06-02
Thanks for the info, robc02. Yes, I've been exaggerating a bit with the resolutions, I just wanted to see what this scanner is capable of :). However, there IS one problem with the scanning programs. I know 300dpi is enough for most purposes when scanning photos. However, having a scanner with 4800dpi capability, one would like to occasionally scan a photo at a higher resolution (if only to then scale it down to 300dpi, after some refocusing and tweaking, and thus gain better depth and quality than using 300dpi from the start). And why not have a larger printing size than the original photo? (300dpi is good for merely copying with basically the same size). The problem is, with XSANE the next resolution after 300 is 2400 (it's too high and the program won't let you do it anyway), KOOKA also only has 300, 2400 and 4800 (it will allow you to scan at the higher resolutions, but at 2400dpi it will take ages and then your graphics application will basically die when you try so much as scale it down, unless you have some high-end hardware). ISCAN has a nice gradual progression of resolutions, but that's actually quite useless because IT WON'T ALLOW YOU TO SCAN ANYTHING AS BIG (OR AS SMALL) AS A 15X10cm PHOTO AT A RESOLUTION HIGHER THAN 300dpi! So I don't know what all those higher resolutions are for, because if you want to scan negatives or slides, you'd go straight on to 2400 or 4800.
It won't even allow you to scan greyscale or line-art at over 300dpi! That's just ridiculous, what a waste of resources! Any idea how to get around this?

---

### Post by robc02 on 2008-06-02
I don't have very much experience. I have only used the higher resolutions for scanning individual slides or negatives. Most of my scanning has been pretty utilitarian stuff - scanning documents for records or to email to people - so lower resolutions are fine, and the V200 and xsane have proved great tools for the job. I haven't even tried Iscan!

---

### Post by boddhisatva on 2008-06-03
Thanks anyway, robc02. Different needs different problems :). I'm mainly interested in scanning photos and tweaking them. **I've found a partial solution to the problem** so I can scan 15x10 photos at whatever resolution I want. It appears iscan only takes into account the **horizontal** size of the selected area when judging if the image is too big, so the way to go is to **always place the photos vertically**. I scanned some old photos at 600 and 1200dpi and they came out fine, without overburdening the system. Especially one poorer-quality photo benefited a lot from this - in the original I had problems recognizing the faces (it's a group photo taken from a distance with a cheap camera, a bit out of focus and faded, with poor colours), after some tweaking in GIMP (refocusing, changing colour levels and curves, contrast, selective gaussian blurring, resizing, etc.) I obtained quite a natural-looking photo and I could clearly recognize the people in the photo! :) Quite a flashback :)

---

### Post by godishere on 2008-07-02
im new to all of this. i have ubuntu 8.04 amd64 and epson v200 scanner. i have iscan and iscan-plugin packages for i386.rpm. now how do i get that to work on my amd64? please help my!

---

### Post by Rhubarb on 2008-07-07
> **godishere said:**
> im new to all of this. i have ubuntu 8.04 amd64 and epson v200 scanner. i have iscan and iscan-plugin packages for i386.rpm. now how do i get that to work on my amd64? please help my!
There is no easy way to get this working with 64bit Ubuntu.
If you're up for a bit of a challenge, you could follow this:
[http://ubuntuforums.org/showpost.php?p=4926086&postcount=44](http://ubuntuforums.org/showpost.php?p=4926086&postcount=44)
If possible, you may have to resort to using 32bit Ubuntu to get your V200 scanner working.

It's a real shame about this.
We would benefit if Epson started supporting 64bit linux drivers / open sourcing their drivers / collaborated with SANE.

---

### Post by SlaughterDog on 2008-07-22
I'm on Hardy and I just bought an Epson V200 Photo. 

However, XSane doesn't have an ICM file already loaded into it, so I can't scan in color. Can anyone help me?

Edit: Oh stupid me, I don't need to use ICM ^^;

---

### Post by boddhisatva on 2008-07-23
> **SlaughterDog said:**
> I'm on Hardy and I just bought an Epson V200 Photo. 

However, XSane doesn't have an ICM file already loaded into it, so I can't scan in color. Can anyone help me?

Edit: Oh stupid me, I don't need to use ICM ^^;

I'm subscribed to this thread and in my email I got this instead of the above message:
"I'm using Hardy and can't get this to work. I just got the Epson V200 Photo. Where I run into trouble is there is no 45-libsane.rules file."
So I don't know what your problem is exactly.
If you're on Hardy, you don't have to worry about 45-libsane.rules.

---

