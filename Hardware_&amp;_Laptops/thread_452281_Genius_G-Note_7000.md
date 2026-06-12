---
title: "Genius G-Note 7000"
date: 2007-05-23
forum: Hardware &amp; Laptops
---

### Post by AAM on 2007-05-23
has anyone out there got one of these devices and successfully used it with Ubuntu (or any Linux distro)?

anyone have the courage to step me through the process of trying to get it to work?

---

### Post by AAM on 2007-05-23
Point 1:
when plugged in to the USB port, it is recognised as a USB drive. Hooray!

The file is of the TOR suffix. Anyone have any idea about this?

---

### Post by AAM on 2007-05-23
When NOT plugged in, the device will store handwriting and pictures onto a small flash drive. The storage medium can be accessed through automatic udev loading. The file type is TOP (not TOR as I said before!). This appears to be a proprietary image format. I can't find a reference on Googling.

When the device is plugged in with the USB, it is externally powered and acts aas a tablet. Ubuntu 7.04 detected it immediately and responded 'appropriately'. The cursor moves when the pen moves and touching the pad is equivalent to a double click or click and hold. The scaling seems to be wrong however. The coordinate reference does not seem to be static. But I shall investigate how to do this on a Wacom, which  might be the same.

To access TOP files, I have installed the defauly Windows (2000 compatible) software under WINE and will report back later.

PS: make sure the pen has a new battery before you begin and take out the battery when finished.

---

### Post by AAM on 2007-05-23
Update: well, all has gone remarkably well!

The default software needed is the drivers, and the My Ink software. To run this you cd into the WINE directory ( cd ~/.wine/drive_c/Program\ Files/MyInk) and from that directory then run the EXE under WINE (~$ wine My\ Ink.exe). This will allow you to read the files (from "media/disk') and convert them to JPG, BMP or PDF files. These files are saved in a directory under /home/myname/My Ink Converted Files/

---

### Post by AAM on 2007-05-23
some additional data, although no successful outcome yet.


lsusb > **ID 172f:0027** but no name! and device captured as [B]/dev/hiddev0
sudo cat /sys/bus/usb/devices/*/products[/B] gives the name "**Digital Ink Pad**"

So I am pursuing the **wizardpen** configuration options to be able to configure screen size and stylus pressure, Will relate back and give conclusion.

---

### Post by therealwireless on 2007-10-31
The issue of the "scaling being wrong" is perhaps that the the resolution of the device is 150dpi and your screen is not... 72, 80, 96dpi....  Just a guess.

Any further progress on this product?

---

### Post by davim on 2008-01-09
try this [http://community.livejournal.com/ubuntu_users/275396.html](http://community.livejournal.com/ubuntu_users/275396.html)

---

### Post by mohabe on 2008-01-22
Hi guys, thankx for the info
I've got a G-note 7000 on order and should be arriving on Monday. Keep the info coming and I'll post how it went on mine! I was looking for OCR software to read the TOP files but it looks like I'll have to fork out the dough on MyScript

---

### Post by mohabe on 2008-02-03
Hi all. 
Got the G-note. Got it installed. It is recognized and works as Tablet.
Followed instructions (installed drivers and MyInk) but MyInk not working
On typing wine ... I get
> err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\Program Files\\MyInk\\My Ink.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\MyInk\\My Ink.exe" failed, status c0000135

It looks like the installation did not work right. I've tried uninstalling and reinstalling but nothing is working.

Any suggestions/help?

---

### Post by ksh1 on 2008-04-06
Note sure if anyone is still reading this thread but the following perl script seems to work for me. It might be lacking refinement and perl purists might cry but hopefully it will help someone.



>>

#!/usr/bin/perl
# Converts Genius G-note 7000 file to SVG file
# 
open(FILE,$ARGV[0]);    # filename
binmode(FILE);          # it is a binary file
read(FILE,$header,32);  # ignore header
$pen_up = 1;
#print .svg header
print "<?xml version=\"1.0\" standalone=\"no\"?>
<!DOCTYPE svg PUBLIC \"-//W3C//DTD SVG 1.1//EN\" 
  \"http://www.w3.org/Graphics/SVG/1.1/DTD/svg11.dtd\">
<svg width=\"20cm\" height=\"30cm\" 
     viewBox=\"0 0 8500 11000\" version=\"1.1\"
     xmlns=\"http://www.w3.org/2000/svg\">\n";
print "<path d=\"";

while(read(FILE,$point,6)) {
        @byte = unpack ("C*",$point);
        $y = $byte[1] + $byte[2] * 256;
        $x = $byte[3] + $byte[4] * 256;
        $p = $byte[0];

        if($pen_up==1)
                {
                printf("M %d %d ",$x,11000-$y);
                $pen_up=0;
                }
        else
                {
                printf("L %d %d \n",$x,11000-$y);
                }

        if($p==0)
                {
                $pen_up=1;
                }
}

print "\"\n fill=\"none\" stroke=\"black\" stroke-width=\"12\" />\n</svg>\n";

---

### Post by mohabe on 2008-04-08
Hi
I'm still checking it! 
I see that you suggest writing Perl code to convert the file to SVG. I have two questions
a) I assume your code goes into a file and the new file becomes executable ... no? 
How would you execute it? (as you can see I'm not much of a Perl user)
b) Once I have the file in SVG format, how do I convert it into text?
Thankx

---

### Post by ksh1 on 2008-04-08
Here are some simple instructions..

A>  Save the text to a file - top2svg.pl for example. (I used vi but you could equally use gedit etc)

make sure the first line says "#!/usr/bin/perl". 

Then change the permissions to make it executable 

[prompt] chmod +x top2svg.pl (for example).

Then run it and re-direct the output to a new file 

[prompt] top2svg.pl A01.TOP > A01.svg. 

the file can then be viewed/imported into documents etc etc,

B> Not sure what you mean here... I've just use it to get .TOP files into a viewable format for firefox etc.

Hope this helps. Good luck.

---

### Post by leha on 2008-04-26
Hi, 

I am not sure if anybody is still interested in this but I put some code on google (not finished but in more or less workable state) that works with .dnt files (it is a file format for G-Note 7100). .top and .dnt files look very much alike so if you need something better then the perl script above look at [http://code.google.com/p/g-note-utils/](http://code.google.com/p/g-note-utils/) I believe it is easy to add support for top files but I have neither sample files nor format description. 

G-note's software works fine in wine on my system (only on 32 bit ubuntu) so probably there is not much need in linux utils.

---

