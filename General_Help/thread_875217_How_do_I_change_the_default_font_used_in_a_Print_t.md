---
title: "How do I change the default font used in a Print to PDF file?"
date: 2008-07-30
forum: General Help
---

### Post by wayfarer_boy on 2008-07-30
At the moment, each time I export an invoice from GNUCash, the PDF created uses the DejaVuSerif font at a rather unsightly 14pt+ size. I've tried creating a cups-pdf printer, manually editing the pdd file, copying fonts (both type1 and ttf) to the cups fonts directory, editing the cups .conf files in /etc, editing the conf.d font files created by fc-cache, and several other more absurd ideas, but none have changed the typeface of the output.pdf file.

I posted the exact same question 1 year and 2 weeks ago today... strange how a problem comes around in a seasonal way!  Nobody replied to the last post, but I'm hoping there may be more readers this year!

Anyone have any ideas? Thanks in advance.

BTW, when I say 'export' from GNUCash, I mean I go to Print, then choose 'Create a PDF document' from the print dialog.

---

### Post by cmnorton on 2008-07-31
This is not your answer, but perhaps a guide to getting closer to your answer.

If you look in /etc/cupsd/cups-pdf.conf, you'll see references to GSCall. I believe you can change the font size by changing how cups-pdf calls gs (Ghostscript). Here is one link; I bet there are some others in these forums as well. Just search for Ghostscript and font.

[http://www.infres.enst.fr/~demaille/a2ps/doc-4.10/a2ps_11.html](http://www.infres.enst.fr/~demaille/a2ps/doc-4.10/a2ps_11.html)

---

### Post by wayfarer_boy on 2008-08-01
Thanks for the tips cmnorton, but it looks like this might be a bug (of sorts):

From [http://members.iinet.com.au/~paulone/gnucash/](http://members.iinet.com.au/~paulone/gnucash/) :

> When printing or print previewing a report, the font changes to an big unchangeable one.  In my case it changes from the screen font of "San Regular 10" to "Serf Regular 12".  This results in very large printed reports.  This is a known bug [http://bugzilla.gnome.org/show_bug.cgi?id=350408](http://bugzilla.gnome.org/show_bug.cgi?id=350408). After looking at GnuCash source code for a while I came to the conclusion the problem was actual with libgtkhtml3.8.

It appears that GnomePrint doesn't have a settable default font and in libgtkhtml3.8 when the required font is the default the pango attrs for font face and size are not set.  The result is that most text is printed in GnomePrint's fixed default of "Serif Regular 12".  My patch changes this to explicitly set the pango attrs for all fonts resulting with all items printed as expected.

This patch is now more then a year old and still not fixed upstream at libgtkhtml3.8.  You can see if its fixed here htmltext.c.  Upstream for libgtkhtml3.8 would not apply the patch because they are only interested in evolution and the gnucash developers have been promising to change from libgtkhtml3.8.  See you in another year.


Haha - 'see you in another year'!  Anyway, I'm gonna patch libgtkhtml and see what happens.  Thanks for the reply tho.

---

### Post by wayfarer_boy on 2008-08-01
Success!  The patches worked.  I didn't bother applying them, as paul ([http://members.iinet.com.au/~paulone/gnucash/](http://members.iinet.com.au/~paulone/gnucash/)) supplies Hardy rpm packages.  Just go to [http://members.iinet.net.au/~paulone/gnucash/download.html](http://members.iinet.net.au/~paulone/gnucash/download.html) and download the 3 packages marked **Required** under *Packages for ubuntu hardy 8.04LTS*.

Then, do the following:
[LIST=1]
[*]Remove gnucash (this will also remove unused dependencies):
```
sudo aptitude remove gnucash
```
[*]Install the dependencies on their own (leaving out libgtkhtml):
```
sudo aptitude install guile-1.6 guile-1.6-slib libfinance-quote-perl libgoffice-0-4 libgoffice-0-common libgsf-gnome-1-114 libhtml-tableextract-perl libofx4 libosp5 slib
```
[*]Run and install each of the downloaded .deb files, starting with libgtkhtml, then gnucash-common, then gnucash
[*]Open GNUCash
[*]Go to Print a report, and you'll see a new Font button to the bottom of the print dialogue
[/LIST]
I've found that you can't just print using any font - I tried Helvetica Neue and gnucash froze and sat and ate all my memory.  It might be to do with whether the font's type1 or truetype, but Im perfectly happy using freesans medium for now.

Hope that helps someone else.

---

### Post by b5baxter on 2008-09-05
Unfortunately the packages don't seem to work in the x64 architecture.  

How do I apply the patch (I haven't applied a patch before)?

---

### Post by wayfarer_boy on 2008-10-08
Sorry about missing your post.  To apply the patch:

[LIST]
[*]Download the source code for libgtkhtml3.8 - you should be able to do this with:```
wget http://archive.ubuntu.com/ubuntu/pool/main/g/gtkhtml3.8/gtkhtml3.8_3.13.5.orig.tar.gz
tar -zxvf gtkhtml3.8_3.13.5.orig.tar.gz
```[*]cd to the source folder and download the patch```
cd libgtkhtml3.8_3.13.5.orig
wget [http://members.iinet.net.au/~paulone/gnucash/print-font-gtkhtml3.8-fix.patch]("http://members.iinet.net.au/%7Epaulone/gnucash/print-font-gtkhtml3.8-fix.patch")
```[*]Follow the "How to patch" instructions here (it talks about patching the linux kernel. but the principle's the same) - [http://www.linuxhq.com/patch-howto.html](http://www.linuxhq.com/patch-howto.html)
[*]Once you've patched the application, compile and install, then do the same steps for the gnucash patches.[/LIST]
Warning: I'm doing this 'blind' as I'm away from my machine at the moment, so please post if you get stuck.

---

