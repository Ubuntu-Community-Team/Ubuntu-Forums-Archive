---
title: "Samsung CLP-300 color profile problem"
date: 2008-08-04
forum: Hardware
---

### Post by couzin2000 on 2008-08-04
I purchased the **Samsung CLP-300** a little before Xmas tlast year, so the printer is not 8 months old yet. When purchased, I took it out the box and plugged it in. When the wire connected, *it took all of 7 seconds to install the CUPS system and required drivers automatically* - I didn't have to do anything.

Now I've run into a very complex problem; I'm using **Photoshop CS** in a VirtualBox install to create color-managed pictures. I can then open them in **Gimp** and they are effectively color-managed as well, and appear exactly the same in one app screen and the next. So color management works... for my LCD monitor.

Not so for my printer. The images are very dark, somber even. I figured I needed to install an appropriate ICC or ICM color profile, so I looked around, and I couldn't find any info on it.

In finally resorted to [Google]("http://www.google.ca/search?q=icm+clp-300&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a"), and found the following links:
[LIST]
[*][http://www.linuxprinting.org/show_printer.cgi?recnum=Samsung-CLP-300]("http://www.linuxprinting.org/show_printer.cgi?recnum=Samsung-CLP-300")
[*][http://foo2qpdl.rkkda.com/]("http://foo2qpdl.rkkda.com/")
[/LIST]

The first link explains that the tester used [FONT="Courier New"]cups-calibrate[/FONT] to manage the color on the printer. I ran that, but then I discovered the color profile would not affect the CUPS driver unless I used a print plugin with Gimp called "**Print with Gutenprint**". So I installed it. I got the plugin to appear, I can print documents, but the profiling created with [FONT="Courier New"]cups-calibrate[/FONT] is not being used. I get very somber colors, on every print - and they are all the same. There is no color management.

To me, it looks like CUPS doesn't use color management running in Gutenprint, in foo2qpdl, or in any other wrapper or driver. As explained by [FONT="Courier New"]cups-calibrate[/FONT], I've added the [FONT="Courier New"]*colorProfile[/FONT] line to [FONT="Courier New"]/etc/cups/PDD/CLP-300.pdd[/FONT] - with no results at all.

I'd like to know - I share this printer with my laptop. If I must change the CUPS system to Ghostscript, or something like that, It'll be difficult for me since I am not very experienced in stuff like that; also, I must know that this sharing will work over NFS with my laptop (running the same Ubuntu version).

If you need more details, please ask - I need to fix this pronto!

---

### Post by potam on 2008-08-23
Exactly the same problem here. I ended up with an acceptable cupsColorProfile setting, inserted into /etc/cups/PDD/CLP-300.pdd, and tried printing. Like it was not even there, none of the gnome programs printed with the new color settings. The example pictures printed by cups-calibrate at the end of the process are perfect.

---

### Post by potam on 2008-08-23
One possible solution I found is to buy a custom profile. Process is simple: you got one or two images, you print them without color correction, send the paper back via snail mail, and get your custom profile via email. Worth to try, costs ~10$. Details described at the end of this document: [http://foo2zjs.rkkda.com/INSTALL]("http://foo2zjs.rkkda.com/INSTALL")

---

### Post by qole on 2008-08-23
Perhaps this thread can help you? 

[[SOLVED] CLP-300 Color Range is Wrong]("http://ubuntuforums.org/showthread.php?t=857697")

EDIT: Yes, it helped enormously. The key is to open a terminal and do this:

```

cd /usr/share/foo2qpdl/icm/
sudo getweb 300

```

---

### Post by potam on 2008-08-24
> **qole said:**
> 
```

cd /usr/share/foo2qpdl/icm/
sudo getweb 300

```

I already have this icm file, for me it's color correction is not acceptable, dark photos, etc... The problem is, as described in some forums, color correction is for one kind of ink and one kind of paper-type. Perfect for the creator, acceptable for some people, and unacceptable for others.

---

### Post by qole on 2008-08-24
The original poster was not able to get colour correction working at all. I was just saying where and how the colour correction file could be obtained. The printer, as installed by Ubuntu, does not have any colour correction. My oranges were printing as dark brown. After installing the ICM file, my oranges were orange again, albeit a dark orange.

I think the ICM file leaves something to be desired, also. 

Please note that cups-calibrate, as stated in the opening text when you run that program, only works with certain printer drivers, specifically "Gutenprint CUPS or ESP Print Pro drivers". The default CLP-300 driver is not one of these, it is the [foo2qpdl driver]("http://foo2qpdl.rkkda.com/"). According to the [OpenPrinting link]("http://www.linuxprinting.org/show_printer.cgi?recnum=Samsung-CLP-300") in the original post, you need to use the [Splix driver]("http://splix.ap2c.org/") "built with jbigkit (which might not be included in your distro due to patent issues, so you might need to build it by yourself)" if you want the cups-calibrate results to have any effect.

EDIT: I notice that the manual for foo2qpdl mentions the ability to change the gamma. This might improve the darkness issues that we're having:

> 
&#8722;G gamma-file.ps
      Prepend gamma-file.ps to the Postscript input to perform color correction using the setcolortransfer Postscript operator. For example, the file might contain:
      {0.333 exp} {0.333 exp} {0.333 exp} {0.333 exp} setcolortransfer


---

### Post by couzin2000 on 2008-08-25
new gamma didn't change a thing... I did implement many things in foo2qpdl, and there is some improvement - but not enough for my taste. Any other suggestions?

---

### Post by qole on 2008-08-25
No more suggestions, I've resigned myself to printing to my CLP-300 from Windows until someone:
[LIST=1]
[*]produces a reasonable ICM file
[*]produces a reasonable CRD file ("The CRD-based method was tuned for Ghostscript and the foo2qpdl engine, and produces better colors.")
[*]Shows me how to calibrate this printer with open source software.
[/LIST]

---

### Post by qole on 2008-08-25
Just a note, I'm not near my printer at the moment, so I can't test anything out. In order to make changes to colour management, you have to mess with the PPD file like so:

in /etc/cups/ppd/CLP-300.ppd :

```

*OpenGroup: Adjustment/Adjustment

*OpenUI *ICM/ICM Color Profile: PickOne
*FoomaticRIPOption ICM: enum CmdLine A
*OrderDependency: 300 AnySetup *ICM
*DefaultICM: clp300
*ICM clp300/CLP-300: "%% FoomaticRIPOptionSetting: ICM=clp300"
*FoomaticRIPOptionSetting ICM=clp300: "-C10 -Gsamclp300-0.icm "
*ICM photo/Photos: "%% FoomaticRIPOptionSetting: ICM=photo"
*FoomaticRIPOptionSetting ICM=photo: "-C1 "
*ICM photext/Photos and Text: "%% FoomaticRIPOptionSetting: ICM=photext"
*FoomaticRIPOptionSetting ICM=photext: "-C2 "
*ICM grph/Graphics and Text: "%% FoomaticRIPOptionSetting: ICM=grph"
*FoomaticRIPOptionSetting ICM=grph: "-C3 "
*ICM none/No ICM color correction: "%% FoomaticRIPOptionSetting: ICM=none"
*FoomaticRIPOptionSetting ICM=none: "-C10 -Gnone.icm "
*CloseUI: *ICM

*CloseGroup: Adjustment

```

Here, I've deleted all of the colour profiles that were useless and I've added a few that might work according to the [manual]("http://foo2zjs.rkkda.com/manual.pdf"), namely the CRD profiles:

> 
&#8722;C colormode
[INDENT]Color correction mode [0].
0 Best compromise
1 Photos (using m2300w CRDs)
2 Photos and text (using m2300w CRDs)
3 Graphics and text (using m2300w CRDs)
10 ICM color profile (using -G *.icm file)[/INDENT]


I'm not convinced that the -C parameter is even used here, despite the fact that it is included in the command line of the PPD. It might be silently ignored. I think the best bet is to figure out how to include gamma info.

**couzin2000:**

How did you test your new gamma? Do you have a .ps file with some good gamma settings in it? Could you post it here? I wonder if you can do the -G parameter twice, or do you have to concatenate / prepend / append the gamma settings to the samclp300-0.icm file?

---

### Post by qole on 2008-08-26
Good news! 

The "Photos" setting (-C1) in my modified PPD produces a much more accurate printout. It still isn't quite as accurate as the Windows printout, but it is better than the Samsung ICM.

I copied a bunch of files into my crd folder, if you do not get any improvement, then post here and I'll tell you what I copied.

---

### Post by couzin2000 on 2008-08-26
> **qole said:**
> 
**couzin2000:**

How did you test your new gamma? Do you have a .ps file with some good gamma settings in it? Could you post it here? I wonder if you can do the -G parameter twice, or do you have to concatenate / prepend / append the gamma settings to the samclp300-0.icm file?

What I actually did was reload the new version of [FONT="Courier New"]foo2qpdl[/FONT] from my second link (as stated in my first post), and then I went ahead and re-ran the instructions for Gutenprint and the [FONT="Courier New"]cups-calibrate[/FONT] command. At this point, it did have an effect, but I have a feeling that the calibration process isn't as precise as it should be. I still get dark results, but they *are* a little bit better. However, it's just not enough. Let's just say I wouldn't use the settings I have now to print pics to go in a photo album - the color rendering isn't acurate enough.

I don't remember actually playing in the files you mention ([FONT="Courier New"]samclp300-0.icm[/FONT] and the likes), all I did was really play around with the settings with [FONT="Courier New"]cups-calibrate[/FONT]. I haven't had a chance to use these posts and all the info you guys have sent my way, but I will definitely try again as soon as I'm near my printer.

For the record, I find this way of proceeding very laborious. It's a shame that it isn't as easy as "driver-install" and "print". Unfortunately, this is what we're given, but at least we can work together to resolve these issues, so thanks very much for your help - keep sending some!

---

### Post by potam on 2008-08-26
I ordered a custom ICM profile for my printer, and as soon as it arrives I will share with you.

---

### Post by qole on 2008-08-27
Here is my modified PPD file. 

Install by unzipping and putting this file in /etc/cups/ppd

Choose "Photos" in the color management area of the printer dialog and then tell me, is it not much better?

---

### Post by babusar on 2008-08-27
> **qole said:**
> Here is my modified PPD file. 

Install by unzipping and putting this file in /etc/cups/ppd

Choose "Photos" in the color management area of the printer dialog and then tell me, is it not much better?
That makes a big difference! Thanks

---

### Post by potam on 2008-09-04
So my ordered ICC profile arrived, and I am very satisfied with the result, and of course I share it with you now. But again,please note that this profile is made for my printer, my ink, my paper. It can be perfect for you, acceptable for you, and there is a chance that it is unacceptable for you. Todo: replace /usr/share/foo2qpdl/icm/samclp300-0.icm with this file: [samclp300-0.icm]("http://potam.extra.hu/upload/samsung/samclp300-0.icm")

---

### Post by babusar on 2008-09-06
> **potam said:**
> So my ordered ICC profile arrived, and I am very satisfied with the result, and of course I share it with you now. But again,please note that this profile is made for my printer, my ink, my paper. It can be perfect for you, acceptable for you, and there is a chance that it is unacceptable for you. Todo: replace /usr/share/foo2qpdl/icm/samclp300-0.icm with this file: [samclp300-0.icm]("http://potam.extra.hu/upload/samsung/samclp300-0.icm")
I've used your .icm file along with qole's .ppd file and the printing is much improved. Moran taing!

---

### Post by Dr.Fritz on 2008-09-19
hello, i bought clp-300 4 hours ago and i had the same prob.i used qoles pdd file and the print quality is way better, one thing though, i navigated in the folder where the icm file should be , and nothing was there so i just pasted the custom icm file potam uploaded...

question: what should i do in order to actually use and try that icm? because if i get it correctly, by Choosing "Photos" in the color management area of the printer dialog as qole suggested i dont use the custom icm file... or do i? 

anyways thanks a lot guys for your effort! 

-off topic- i also have a Samsung ML-2010P which is just BW, does any1 happen to know if theres a big or small price difference for text printing? and has any1 figured out how to two-side print with ML-2010P but CLp-300 also? 

sorry for the off topic thingie and thanks in advance :D

EDIT : by saying text printing i mean monochrome of course :P

---

### Post by potam on 2008-09-21
The ppd file defines which icm file is used and when. In qole's ppd profile go to line 367, here begins the icm and profile definitions. 
```

*ICM clp300/CLP-300: "%% FoomaticRIPOptionSetting: ICM=clp300"
*FoomaticRIPOptionSetting ICM=clp300: "-C10 -Gsamclp300-0.icm "

```
As you can see the samclp300-0.icm is only used in clp300 correction mode, not in photo mode. So to use it, just go to printer settings, search for the Adjustment and select CLP-300 as ICM Color Profile.

---

### Post by couzin2000 on 2008-09-21
Thanks for the help guys... so far, the calibration I gave it (as above stated) is as close to reality as I've gotten it... Though I just saw that new post right above mine, so I'm gonna try that one as well, and we'll see what results come out of it. For the record, I've had no time whatsoever as I'm in the middle of my wedding, but I'm getting to that ASAP, since I need to print out pictures. Thanks for hanging on for my replies!

---

### Post by qole on 2008-10-06
Hi Guys,

Here is a new PPD file. This one has several colour correction settings for you to experiment with.

Extract and put the CLP-300.ppd file in /etc/cups/ppd (replace the existing ppd)

**AVAILABLE COLOR CORRECTION SETTINGS IN THIS PRINTER DRIVER:**

*** CLP-300 (official)**

 This is the Samsung ICM you get when you do this:
```

cd /usr/share/foo2qpdl/icm/
sudo getweb 300

```

*** CLP-300 (custom)**

 This is potam's custom ICM; you need to download it from the message above, but instead of replacing the Samsung ICM, rename potam's ICM to [FONT="Lucida Console"]/usr/share/foo2qpdl/icm/samclp300-1.icm[/FONT]

*** Photos**

 This is a very good setting. It doesn't use an ICM at all; it uses a "m2300w CRD profile".
[B]
* Photos and Text
* Graphics and Text
[/B]
I have not tried either of these settings. They are just the other two available CRD profiles.

---

### Post by edt7 on 2008-11-05
> **qole said:**
> Here is my modified PPD file. 

Install by unzipping and putting this file in /etc/cups/ppd

Choose "Photos" in the color management area of the printer dialog and then tell me, is it not much better?

sorry to sound thick but i can't find /etc/cups/ppd on my pc, but would really like to try these profiles to improve my printing, can someone please give a more detail way of installing these for me

---

### Post by FabriceV on 2008-11-16
Dear all,

The custom icm greatly enhances the results.
The custom .ppd did not enhances the (my own!) results (in fact, most of the profiles gave extremely bad results).
Thus I have used the default .ppd and the custom .icm.

I had like to point out that you can adjust hardware properties of clp-300 directly through Synchtru. You can make final adjustments config/colors and use the config/altitude too (Logically, if you want to decrease saturation, indicate an higher altitude than really experienced).

Regards.

---

### Post by qole on 2008-11-27
> **FabriceV said:**
> Dear all,

The custom icm greatly enhances the results.
The custom .ppd did not enhances the (my own!) results (in fact, most of the profiles gave extremely bad results).
Thus I have used the default .ppd and the custom .icm.

I had like to point out that you can adjust hardware properties of clp-300 directly through Synchtru. You can make final adjustments config/colors and use the config/altitude too (Logically, if you want to decrease saturation, indicate an higher altitude than really experienced).

Regards.

My custom .ppd works great with the custom .icm :)
Just follow the instructions.

---

### Post by qole on 2009-10-19
> **potam said:**
> So my ordered ICC profile arrived, and I am very satisfied with the result, and of course I share it with you now. But again,please note that this profile is made for my printer, my ink, my paper. It can be perfect for you, acceptable for you, and there is a chance that it is unacceptable for you. Todo: replace /usr/share/foo2qpdl/icm/samclp300-0.icm with this file: [samclp300-0.icm]("http://potam.extra.hu/upload/samsung/samclp300-0.icm")

I've reinstalled Ubuntu, and I need this file again... Any chance of making it available for us again?

---

### Post by potam on 2009-11-01
The link works for me. Do you have problem downloading it?

---

### Post by potam on 2009-11-01
[SIZE="4"]Update for Karmic Koala users[/SIZE]:
No need to install the foo2qpdl driver, just plug in the printer, Karmic automatically installs everything, but the icm profiles (none of them!).
First, for me the printer was installed as monochrome, change it to color in administration/printer, and change the resolution to 1200x1200 dpi!

Todo:  _[Download my ICM profile]("http://potam.extra.hu/upload/samsung/samclp300-0.icm")_ (please report if you have download problems, I will upload then elsewhere), and put it into /usr/share/foo2qpdl/icm folder (this folder was empty for me!), and you are done.
Recommended _[printer test file]("http://www.donporter.net/NewSchool/Color/Examples/Printer%20Test%20file.jpg")_.

---

### Post by qole on 2010-01-02
potam: thanks, it is working again for me! I've saved a copy just in case ;)

---

### Post by Yva on 2010-02-21
It's weird. The icm file corrected the color bias but the photos are entirely "pixelized"/"dotted". I'll try to scan the page. Any ideas where it could comes from?

---

### Post by potam on 2010-02-22
> **Yva said:**
> It's weird. The icm file corrected the color bias but the photos are entirely "pixelized"/"dotted". I'll try to scan the page. Any ideas where it could comes from?

Please scan the page and post it.

---

### Post by potam on 2010-03-29
Hello all,

The link I provided to download the ICM file from, will be unavailable soon. Use [this link]("http://upload.pogany.info/index.php?dir=Samsung_CLP-300/&file=samclp300-0.icm") instead! Bonus: [this ICM file]("http://upload.pogany.info/index.php?dir=Samsung_CLP-300/&file=Tamas_Pogany_CLP-300.icm") is made for Windows 7, same printer. You can experiment with it.

---

### Post by snop on 2010-07-21
The links seem to be unavailable. Can someone repost the file, please?

---

### Post by potam on 2010-07-25
Ok, new link, my new hosting company doesn't allow to download binary files directly, so download the two icms from here as a zip file: [http://upload.pogany.info/upload/Samsung_CLP-300/icm.zip](http://upload.pogany.info/upload/Samsung_CLP-300/icm.zip)

---

### Post by digital-daniel on 2010-12-13
Thank you so much. 
Put the Pdd in the cups pdd folder and unzipped the icm files into the icm folder

The print out with "ICM Text" and "ICM Photos" is perfect for my use.  

I couldn't get the "Photo and Text" and "Graphic and Text" to work though.  Is there anything I need to do to get these to work?

---

### Post by potam on 2010-12-23
Personally I don't have any experience with ppd files. Maybe you should drop a pm to "qole", he created the first ppd file (first page of this thread)

---

### Post by qole on 2011-03-09
I think I prefer the "color photos" profile better than the potam custom one. The custom icm from potam is a bit too dark and a bit too red. It is much better than 

As for the "photo and text" and "graphic and text" settings, I confess I've never tried them myself. They are just CRD profile settings from the foomatic manual, as I stated in [this post]("http://ubuntuforums.org/showthread.php?p=5662310#post5662310"). Maybe the only setting that is supported is the first one, "photo"...

---

### Post by notte on 2011-03-30
Ottimo! Funziona benissimo anche su Maverick. La stampa senza questo icm è orribile

Perfect! Printing without this icm is ugly on Maverick too.

---

