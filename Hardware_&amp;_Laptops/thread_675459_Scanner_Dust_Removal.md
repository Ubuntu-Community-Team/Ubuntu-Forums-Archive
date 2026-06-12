---
title: "Scanner Dust Removal"
date: 2008-01-22
forum: Hardware &amp; Laptops
---

### Post by arigram on 2008-01-22
Is there a way to use the dust removal capabilities of my Epson Perfection 4990 Photo scanner with SANE?
Is it still developed? 
Its missing some advanced options that I get with the Windows Epson Scan utility including dust removal, sharpening, print pattern removal, etc.

---

### Post by Whiffle on 2008-01-22
Can't really help you with sane, as I don't use it.  I do have a canon 8800f working under Virtualbox with XP and it works very very nicely.  If you have an old copy of windows laying around that makes for a pretty good option.

---

### Post by TeaSwigger on 2008-01-22
Unfortunately I can't help, in fact I have an old scanner I can't use in Linux so far. The ball is in Epson's court, they are the ones preventing you from using it on anything but MicroSoft product. Be sure to tell Epson. For instance that you expect disclosure if they're owned by MicroSoft, because if they're not you request they accomadate the use the hardware you paid them for on what you choose to use it on. A Linux driver at the least. Sure it might be ignored, but I told the maker of mine, HP, as all we can do is try.

---

### Post by arigram on 2008-01-23
That is quite unfortunate, as the dust removal is very important for scanning, especially professional and batch scanning. I shudder to think I will have to use Windows just for that.

Some notes though:

1) I do not think it is Epson related. The SANE driver is marked as "Complete" and the features I mentioned are found in other scanners as well.
2) Searching through the web, there is mention of dust removal using infra-red (as scanners do it) with SANE but the messages are quite old and not clear in how it is applied or working.

Are there any professional photographers or graphic artists that scan and can shed some light on this subject?

---

### Post by arigram on 2008-02-12
So, I guess SANE and XSane are dead and the only way to scan professionally is through Windows.
:(

---

### Post by oldsoundguy on 2008-02-12
my brother abandoned using his Epson to scan EVEN IN WINDOZE!  it is a "good enough" scanner for most, but when you have to do an enlargement, it leaves a lot to be desired.  And he needs that option. HP still makes a better quality unit! (and you can physically CLEAN the HP with a bit of effort, so "dust" is not as much a  problem.
 And FORGET Lexmark unless you find one made on Wednesday!)

---

### Post by phr0ze on 2008-02-12
I think he means dust on the slide/picture not the scanner.

---

### Post by arigram on 2008-02-13
> **oldsoundguy said:**
> my brother abandoned using his Epson to scan EVEN IN WINDOZE!  it is a "good enough" scanner for most, but when you have to do an enlargement, it leaves a lot to be desired.  And he needs that option. HP still makes a better quality unit! (and you can physically CLEAN the HP with a bit of effort, so "dust" is not as much a  problem.
 And FORGET Lexmark unless you find one made on Wednesday!)

The Epson 4990 is a really fine piece of equipment for its price. Plus you are not mentioning any models, just brand names which are completely vague. Anyway, that is not the point of this thread to compare hardware. And I won't even mention drum scanner support.

Of course I can clean the scanner glass, the print and the negatives, but that is besides the point, as often particles escape and go on the glass anyway.

All modern scanners include some hardware 3D-IR ability to remove dust and its very important when you are doing batch scanning of negatives or even a few prints, especially in a professional environment. Touching up with Gimp is much more time and effort consuming and might not give the same results.

So, my question stands:
Nobody uses Linux for serious scanning work?

---

### Post by Rhubarb on 2008-02-13
This may not be perfect, but there is a command line tool that may help you with getting some dust off many image files in a batch conversion.

```
sudo aptitude install imagemagick
```

Then you try the despeckle filter (which may help - I haven't tried this out just yet, I'm currently researching this so I can do batch scanning of slides myself, as the windows scanning software isn't nearly as powerful and flexible as the tools available to us in ubuntu).

```
convert input_image.png -despeckle output_image.png
```
This will just work with one file
There are guides somewhere on the internet that tell you how to use the imagemagick tools to work with multiple files (for batch processing) in a slightly longer syntax.

This is from the imagemagick website:
[http://www.imagemagick.org/script/command-line-options.php#despeckle](http://www.imagemagick.org/script/command-line-options.php#despeckle)

To see progress about batch scanning and techniques I and a few others have discovered, see this thread:
[http://ubuntuforums.org/showthread.php?t=627650](http://ubuntuforums.org/showthread.php?t=627650)

---

### Post by oldsoundguy on 2008-02-13
you did not mention you are using it for PHOTOGRAPHY ..
As another suggestion you could try using Gimp as your photo manipulation program.  It is so close to Photo Shop, that if it wasn't free, they would be getting sued and hauled into court.  One of the brushes is an artifact remover, another is a spot healing brush.  

NOT the easiest of programs to learn, but then again, neither is Photo Shop, but the documentation for it on line for it is outstanding.

Not sure if you can use it in batch, though.

Photo Shop has a "brush" that is NOT a brush that removes dust artifacts from an image left by dust that may be on the sensor in the camera .. look to have Gimp have that same brush on an update very soon as it was available on CS2.

---

### Post by arigram on 2008-02-13
I think I mentioned that I use Gimp (or many other programs, I have been doing CG for almost twenty years now). Photo manipulation software is not what I am looking for.

Modern scanners have a function that uses Infrared beams from the lens to read the glass area three dimensionally and pick off the dust from the image area, so its less destructive than applying a filter in an image manipulation program, less time consuming and more automatic.
I think I also mentioned that.

That's why I am looking for answers from someone who knows and uses scanners in a professional graphics and photography environment.

XSane or Sane don't seem to much developed.

---

### Post by ArtInvent on 2008-04-21
> **arigram said:**
> Is there a way to use the dust removal capabilities of my Epson Perfection 4990 Photo scanner with SANE?
Is it still developed? 
Its missing some advanced options that I get with the Windows Epson Scan utility including dust removal, sharpening, print pattern removal, etc.

I actually like XSANE but it's got no IR dust removal built in at this time. Try VueScan Linux version.    [**http://www.hamrick.com**](**http://www.hamrick.com**)     It's not free software, but you have to applaud anyone who writes good Linux software that fills a need. It's cheap and seems to do a pretty good job.  I've tried the Linux demo version on Ubuntu and it works pretty well. It's supposed to have very good dust removal using the scanner's infrared channel. I haven't tried the dust removal yet as my old Epson 2450 Photo doesn't have that feature and it's only 1200dpi.  I just ordered an Epson V500 and plan to do a lot of 35mm slide scanning. I've owned film and flatbed scanners, and I know that effective dust removal would save enormous amounts of time. Basically I would not undertake the project of scanning hundreds of my slides without automatic dust removal working in Ubuntu, and the pieces are now in place.

The other nice thing about these Epson flatbeds is that you can set up a batch of slides and scan them in one go. There's no way I'm feeding one slide at a time into the machine and waiting. I thought about getting a Nikon slide scanner and the available auto slide feeder to do batches. But that's quite expensive and I've heard they don't work that dependably.  XSANE can do batch by setting up zones on the scan area. But I think VueScan looks better and easier in this regard - you can do a preview to see all of the slides on the glass, and then individually adjust the scan area and other parameters for each slide. Very nice.

I've read that there's a way to use XSANE and save the IR channel and do dust removal in Gimp with some special procedure involving a filter. I find this far less satisfactory than having it done at scan time. Also, I prefer to scan in 48 bit color, do color and gamma corrections in photo program and Gimp can't handle 48 bit yet.

Hope this helps.

---

