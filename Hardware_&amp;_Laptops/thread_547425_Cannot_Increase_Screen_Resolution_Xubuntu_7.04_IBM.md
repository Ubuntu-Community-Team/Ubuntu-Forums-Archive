---
title: "Cannot Increase Screen Resolution Xubuntu 7.04 IBM Thinkpad T21 S3 Savage"
date: 2007-09-10
forum: Hardware &amp; Laptops
---

### Post by josephzacker on 2007-09-10
I've had no luck increasing my screen resolution beyond 800x600@60 even after editing xorg.conf both by hand and with dpkg.

Here's my "Screen" section:

Section "Screen"
        Identifier      "Default Screen"
        Device          "S3 Inc. 86C270-294 Savage/IX-MV"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024"
        EndSubSection
EndSection

I'm using the refresh rates as specified by the Thinkpad Installation wiki, and I don't seem to have any other video problems other than video output from both Totem & gxine showing up as a blue field when I switch to TV output using s3switch.  Any suggestions?

---

### Post by jmacbeliever on 2007-10-13
Not sure if you ever figured this one out... but I finally found something that helped me, I had the same symptoms that you described. It turned out not to be the "screen" section, but the  "Monitor" Section. Make sure the following options are listed:

HorizSync       31.5 - 48.5
VertRefresh     50-70

I found this on the ThinkWiki, [http://www.thinkwiki.org/wiki/S3_Savage_IX8](http://www.thinkwiki.org/wiki/S3_Savage_IX8)

That tidbit, along with all the other instructions there, finally made the difference for my T21!

Hope that helps.

---

