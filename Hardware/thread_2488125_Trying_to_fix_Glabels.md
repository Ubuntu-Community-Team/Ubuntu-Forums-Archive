---
title: "Trying to fix Glabels"
date: 2023-06-23
forum: Hardware
---

### Post by jgw on 2023-06-23
I am dealing with Glabels AND Dymo label writer 400 turbo.  I have three specific labels that I will use for this printer.   I was having a problem getting rid of specific, and wrong, labels (to write on in printer, there is one that is just a mess and its screwed up with some others as well).  My thought was to delete everything to do with glabels and re-install.  So, after I had (in theory) deleted the offending labels I reinstalled and the offended labels were still there.  So, does anybody kinow where glables is storing this stuff so I can get rid of offending lables in Glables?  

Thank you................

---

### Post by #&amp;thj^% on 2023-06-23
> **jgw said:**
> So, does anybody kinow where glables is storing this stuff so I can get rid of offending lables in Glables?  

Thank you................
A good start:
```
dpkg -L glabels
/.
/usr
/usr/bin
/usr/bin/glabels-3
/usr/bin/glabels-3-batch
/usr/lib
/usr/lib/x86_64-linux-gnu
/usr/lib/x86_64-linux-gnu/libglabels-3.0.so.8.0.0
/usr/lib/x86_64-linux-gnu/libglbarcode-3.0.so.0.0.0
/usr/share
/usr/share/applications
/usr/share/applications/glabels-3.0.desktop
/usr/share/doc
/usr/share/doc/glabels
/usr/share/doc/glabels/AUTHORS
/usr/share/doc/glabels/NEWS.gz
/usr/share/doc/glabels/README
/usr/share/doc/glabels/TODO
/usr/share/doc/glabels/changelog.Debian.gz
/usr/share/doc/glabels/changelog.gz
/usr/share/doc/glabels/copyright
/usr/share/lintian
/usr/share/lintian/overrides
/usr/share/lintian/overrides/glabels
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/glabels-3.1.gz
/usr/share/metainfo
/usr/share/metainfo/glabels-3.appdata.xml
/usr/share/pixmaps
/usr/share/pixmaps/glabels.xpm
/usr/lib/x86_64-linux-gnu/libglabels-3.0.so.8
/usr/lib/x86_64-linux-gnu/libglbarcode-3.0.so.0
/usr/share/man/man1/glabels-3-batch.1.gz

```
And also set in your home, 
> FILES
       The  $HOME/.config/libglabels/templates directory contains all user-de&#8208;
       fined templates.




---

### Post by jgw on 2023-06-27
I am trying to get a dymo labelwriter 400 turbo to behave.  I have sent two photo.  The first is of two printouts.   The two are:
1" x 2 1/8"          1 x 2.125		30336
1 1/8" x 3.5"       1.125 x 3.500	30252

Both of the first photo were both printed on the 1.125"x3.50"  The one that was complete was told it was on a 1"x2.125"  The one that was told it was on a 1.125x3.50   When I try to print ANYTHING on the larger one it always chops whatever is being printed off at 1/10th of an inch.  This makes no sense to me.

Here are the templates for both of the labels:
<?xml version="1.0"?>
<Glabels-templates xmlns="http://glabels.org/xmlns/3.0/">
  <Template brand="dymo" part="30336" size="Other" width="2.125 in" height="1in" description="Mailing Lables">
    <Label-rectangle id="0" width="2.125 in" height="1in" round="0 in" x_waste="0.002 in" y_waste="0.002 in">
      <Markup-margin size="0.125 in"/>
      <Layout nx="1" ny="1" x0="0.002 in" y0="0.002 in" dx="2.125 in" dy="1.004 in"/>
  </Template>
</Glabels-templates>

<?xml version="1.0"?>
<Glabels-templates xmlns="http://glabels.org/xmlns/3.0/">
  <Template brand="Dymo" part="30252" size="Other" width="3.5in" height="1.125in" description="Dymo Mailing labels">
    <Label-rectangle id="0" width="3.5in" height="1.125in" round="0in" x_waste="0in" y_waste="0in">
      <Markup-margin size="0.125in"/>
      <Layout nx="1" ny="1" x0="0in" y0="0in" dx="3.5in" dy="1.125in"/>
    </Label-rectangle>
  </Template>
</Glabels-templates>

I am, obviously missing something here.  If I tell glabels its a smaller label than the real one then it will print with no problem about 1 inch and then just stops.  I have stodied these two trying to see the difference and why it would cut one off and the other not.  Whyen it things its printing a label that is 3.5"x1.125in it will cut off the printing after about 1 inch.  

I have also searched to find out where the glabels are by number.  The numbers, as far as I can tell are only used 1 time.

I am flat out stuck on this one.

---

