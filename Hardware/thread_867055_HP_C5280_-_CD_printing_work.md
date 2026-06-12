---
title: "HP C5280 - CD printing work?"
date: 2008-07-22
forum: Hardware
---

### Post by timcredible on 2008-07-22
Has anyone got printing to CD working with one of the HP C5280 printers?

Thanks.

---

### Post by phidia on 2008-07-22
According to [this entry]("http://openprinting.org/show_printer.cgi?recnum=HP-Photosmart_C5280") at the openprinting database it's working "perfectly". Have you tried to install the printer and hplip?

---

### Post by timcredible on 2008-07-23
thanks for the link.  i haven't bought the printer yet, wanted to check on the cd printing before buying it.  i was able to find a fedora forum thread where a couple people were working on getting margins correct on the cd printing on this printer, so at only $114US for the printer, I'll probably go ahead and get it.

---

### Post by deanjm1963 on 2008-07-23
I have one myself and it works flawlessly.

The problem with printing to CD/DVD's is most applications have difficulty selecting the cd tray.

The only one I have come across so far that works out of the box is OpenOffice.

I made a template after a lot of trial and error and not to mention a dozen or so printed cd's to get the margins "fairly right", it's good enough and gets the job done.

If you'd like the template drop me a line, it's made in OpenOffice Draw, I generally create artwork in Inkscape and import it into OODraw.

---

### Post by timcredible on 2008-07-23
pm sent.  thanks.

---

### Post by Tang on 2008-07-26
Thanks. I also use an HP C5280, set the printer tray settings in System/Administration/Printing and am at present working with an OO word template I found [here ]("http://andrealazzarotto.com/") that may help with precision

---

### Post by timcredible on 2008-07-27
thanks for all the help.  i bought a c5280 this weekend at sams club ($89US, great price), and will hopefully have time to hook it up in a couple days and try it out.

---

### Post by timcredible on 2008-07-27
i couldn't resist trying out the printer tonight, so here's what I did to get it to work:

1 - start out with deanjm1963 template for openoffice draw
2 - fiddle with it a little and here's the settings I use (it's almost perfect):

Format -> Page
Width: 4.72 inches (120mm)
Height: 4.72 inches (120mm)
Margins: Left: .12 inches, right: .20 inches, Top: .02 inches, Bottom: .25 inches

Then I add a picture (I used the ubuntu cd cover art by a few different people as a test), and right-click on the picture, and set Position and Size to: Position X: 0.00, Position Y: 0.00, Width: 4.62 inches, Height: 4.62 inches.

The i go to print, and change the printer properties to: Paper Size: CD or DVD (120mm) and Paper Tray to CD or DVD tray.  

Now if I someone could tell me how to print in openoffice with zero margins, maybe i could get this absolutely perfect, as it is, there is a very very slight margin all the way around the artwork.

---

### Post by carthom on 2009-01-02
If you have photoshop you could always try grabbing a [cd printing template]("http://www.bcduplication.com/index.php?main_page=templates")  provided by one of the duplication companies

---

### Post by timcredible on 2009-08-01
it worked fine with 8.10 (openoffice 2.x), but it's broken in 9.04 (with openoffice 3.0).  great.......

---

### Post by timcredible on 2009-11-08
i found out the reason it doesn't print in 9.04 is because of hplip.  so i upgraded to the newest, it still doesn't print.  i tried 9.10 karmic, and the cd printing works, but the margins are all changed - oo draw files that worked fine in 8.10 no longer properly, they are all printing lower.  i don't understand why hp keeps messing with their print drivers for the same printer.

---

### Post by Tang on 2009-11-24
> **timcredible said:**
> 
i tried 9.10 karmic, and the cd printing works, but the margins are all changed - oo draw files that worked fine in 8.10 no longer properly, they are all printing lower.  i don't understand why hp keeps messing with their print drivers for the same printer.

Hi again, Tim. C5280 owners may have more luck with HP now that updated win 7 32bit package for HP C5280 presumes this model doesn't even *have* a disk tray.

Having proved an untidy fix for that problem with an advance on Angela Lazzarotto's  copertina Linux Oo template, 
[http://andrealazzarotto.com/](http://andrealazzarotto.com/)  HP asked me to email the modified template and instructions to them, which I did yesterday.

If I do hear back from HP R&D, the first thing I intend to do is point them to this forum.

If anyone is interested, the HP forum link for this printer is @
[http://h30434.www3.hp.com/psg/board/message?board.id=Software&message.id=7458#M7458](http://h30434.www3.hp.com/psg/board/message?board.id=Software&message.id=7458#M7458)

PS: Just rebooted to Ubuntu and back, tried the Win7 template 
in Karmic 32 bit and it printed much the same as the original – margin error in win7 is horizontal, not vertical.

HTH

---

### Post by timcredible on 2009-11-24
i ended up installing the latest linux drivers for the printer via the hp website with 9.04, and although openoffice no longer works at all (it won't even print on the cd/dvd anymore), gimp works pretty well.  glabels works but i can't get the margins figured out - glabels has some pretty hardcoded info about how to print on a cd/dvd and it won't deviate which pushes everything right and down. 

so, to sum up, if you have an hp c5280 or similar, using 9.04 with the drivers that came on the 9.04 CD don't work.  but, using 9.04 with the latest drivers from hp.com works for gimp only.  in 8.04 openoffice worked with the drivers that came on the 8.04 cd.

i applaud hp for making linux drivers, but why not finish them, or re-do the openoffice templates that they used to have a couple years ago?  re-doing the templates would probably take one engineer one day....

---

### Post by Dale61 on 2010-06-04
I hate to bump a thread that is so old, but as I have the same printer and have it set to print with just a small, unprinted edge on the disc, I thought I'd add my settings here.

As I live in Australia, we use metrics.


Format -> Page
       Format -> User
Width: 12.00cm
Height: 12.00cm
Margins: Left: 0.35cm, Right: 0.50 cms,
Top: 0.35 cms, Bottom: 0.50cms
OK

Insert a picture, right-click on the picture.
Position and Size: Position X: -0.20cms, Position Y: -0.20cms.
Width: 11.45 cms, Height: 11.45 cms.
OK

Go to print, and change the printer properties to: Paper Size: CD or DVD (120mm) and Paper Tray to CD or DVD tray.

I used the above settings and my prints were way off centre.  A bit of trial-and-error, a tweak here and a tweak there, and I have it so as there is very little border, but not too much to detract form the final product.

---

### Post by timcredible on 2010-06-04
thanks for the info, i'll try the setting next time i print to a cd.  i bought a new pc recently, it came with windows 7.  i installed the hp software for windows 7, and it doesn't even allow me to print to the cd with it.  it's the only thing i've used windows for.  sad that hp keeps going backwards on their support for this printer, seeing as how i have a laptop with windows xp and the hp software does work for it.

---

### Post by Dale61 on 2010-06-07
> **Dale61 said:**
> I hate to bump a thread that is so old, but as I have the same printer and have it set to print with just a small, unprinted edge on the disc, I thought I'd add my settings here.

As I live in Australia, we use metrics.


Format -> Page
       Format -> User
Width: 12.00cm
Height: 12.00cm
Margins: Left: 0.35cm, Right: 0.50 cms,
Top: 0.35 cms, Bottom: 0.50cms
OK

Insert a picture, right-click on the picture.
Position and Size: Position X: -0.20cms, Position Y: -0.20cms.
Width: 11.45 cms, Height: 11.45 cms.
OK

Go to print, and change the printer properties to: Paper Size: CD or DVD (120mm) and Paper Tray to CD or DVD tray.

I used the above settings and my prints were way off centre.  A bit of trial-and-error, a tweak here and a tweak there, and I have it so as there is very little border, but not too much to detract form the final product.

I've done a little tweaking to my measurements as I've just printed quite a few discs (a little tweak here, a little tweak there, here a tweak, there a tweak, everywhere a tweak tweak - sorry, couldn't resist!). and have new settings.

The page set-up remains the same, however, where it is placed on the page is slightly different than my first set-up.

First, I create my images in GIMP, and are 450 pixels x 450 pixels.

Now, click 'Insert' > Picture > From File, then right-click on the picture.  Make sure you see the green 'handles'.

Position and Size: Position X: -0.35cms, Position Y: -0.20cms.
Width: 11.50 cms, Height: 11.50 cms.
OK

Go to print, and change the printer properties to: Paper Size: CD or DVD (120mm) and Paper Tray to CD or DVD tray.

This now prints on a disc near on perfect.

Make sure you save after your last print.  This ensures you retain the settings without having to do it all over again each time you have a print run.

I should mention that I am running on 10.04, my template is saved in OpenOffice 3.2 (.odg) and my images are created in GIMP 2.6.8.  All are standard installs.

---

### Post by luckyphillipe on 2011-02-20
> **Dale61 said:**
> I've done a little tweaking to my measurements as I've just printed quite a few discs (a little tweak here, a little tweak there, here a tweak, there a tweak, everywhere a tweak tweak - sorry, couldn't resist!). and have new settings.

The page set-up remains the same, however, where it is placed on the page is slightly different than my first set-up.

First, I create my images in GIMP, and are 450 pixels x 450 pixels.

Now, click 'Insert' > Picture > From File, then right-click on the picture.  Make sure you see the green 'handles'.

Position and Size: Position X: -0.35cms, Position Y: -0.20cms.
Width: 11.50 cms, Height: 11.50 cms.
OK

Go to print, and change the printer properties to: Paper Size: CD or DVD (120mm) and Paper Tray to CD or DVD tray.

This now prints on a disc near on perfect.

Make sure you save after your last print.  This ensures you retain the settings without having to do it all over again each time you have a print run.

I should mention that I am running on 10.04, my template is saved in OpenOffice 3.2 (.odg) and my images are created in GIMP 2.6.8.  All are standard installs.
Hi Dale
I'm in Melbourne and I'm running Linux Mint 10 with Open Office 3.2.1 but I can't figure out how to set up the X & Y positions. Can you please send me a how to.
Thanks in advance
Luckyphillipe :)

---

### Post by Dale61 on 2011-02-20
I've replaced that HP printer since posting that, but the X and Y settings are the Horizontal (from left) and Vertical (from top).

We have also upgraded from a single desktop, to each of us having a laptop, so the desktop has been 'converted' back to XP to be used solely as a print server, and all the printing now gets done as per printer software.

The only real help is to go with the settings I used, and then try-and-error to fine tune.  Change the page borders; change the page size; change whatever to see what happens, then when you find what's good for you, save it.

---

### Post by luckyphillipe on 2011-02-24
Hi again Dale
You must think I'm a bit of a dill but I still don't know what to actually point and click to get those X & Y positions. It is probably easy but I haven't used Open Office much and I just can't work it out. Thanks for your patience in advance.
Phill :(

---

### Post by Dale61 on 2011-02-24
G'day Phill.

I've sent you a PM with all the settings I used, and an explanation of how to get to each setting.

I no longer use OpenOffice (LibreOffice for me now) and I no longer use the HP as it was replaced long ago.

---

