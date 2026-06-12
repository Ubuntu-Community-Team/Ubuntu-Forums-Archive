---
title: "changing paper size has no effect"
date: 2008-11-28
forum: Hardware
---

### Post by feitjie on 2008-11-28
Hi to all 

I am trying to setup a epson lq-590 dot matrix printer on ubuntu 8.1
i have managed to install the printer and i am able to print a test page

the problem is, i want to do continuous printing for invoices, but there is no paper size matching my preprinted invoices

if i change it to the closest one on the printer settings it has no effect
the paper stil moves up to a4 size

i have changed the paper size in /etc/papersize to another size but then the printer does not print

Anny help would be appreciated

---

### Post by ideewoww on 2008-11-28
[img]http://www.ideewomen.com/cn/uploads/200811131739540.jpg[/img]The IDee fashion jewelry , accompany women&#8217; life-long beauty.The IDee brand connotation: Individuality, nature, fashion, romantic,

---

### Post by kiridude on 2009-04-01
Did you change the LC_PAPER setting?

---

### Post by FrancoNero on 2009-04-07
I'm using a HP d2560 and nothing i do in printer settings has ANY effect.... bummer...

---

### Post by FrancoNero on 2009-04-09
so yeah sudo gedit /etc/papersize works but... HELLO what's the gui and the printer settings for then if you have to edit a configuration file? this is so ridiculous

---

### Post by nixi on 2009-05-02
I have been trying to control printing on paper sizes such as A3, A2, and A1 on an Epson Stylus Pro 7500, and I'm sorry to say it seems close to futile in Ubuntu. Yet I did manage to print a couple of A1 sized documents by doing this: 

1. deleted and reinstalled the recommended printer driver 
2. entered CUPS gui by [http://localhost:631](http://localhost:631), and set "media size" to "A1"
3. sudo gedit /etc/cups/ppd/printer's-name.ppd, and set StpDefaultPageSize, StpDefaultPageRegion, StpDefaultImageableArea, and StpDefaultPaperDimension to "A1" (they were still "letter" in spite of CUPS)
4. sudo dpkg-reconfigure libpaper1, and selected "A1" (to set /etc/papersize to "a1")
5. opened the documents (pdf) in Evince, selected "A1" from printer properties, and printed them.

So evidently it is possible to print A1 sized documents. However, I also have a standard sized laser printer, and I wanted to print some ordinary A4s. Therefore I typed sudo dpkg-reconfigure libpaper1 again, selected "A4" (to set /etc/papersize to "a4"), selected the laser printer, and managed to print A4 sized documents. 

Later, when I wanted to print those A1 sized documents on the Epson again, I typed sudo dpkg-reconfigure libpaper1, selected "A1", and started the printing.  But this time the document was cropped, as if the system was stuck on "letter", and seemingly indifferent to all the above mentioned settings being set to "A1". I have done the entire procedure from 1 to 5 again, restarted printer, computer, reset power, but the system keeps on cropping the documents indifferent to any user controlled settings. And this is, of course, extremely frustrating. Especially since I use Ubuntu at work.  

Any constructive advice appreciated, thanks!

---

### Post by EKa on 2009-05-12
Hi,

sorry, I'm offering just sympathy. For me it took about 6 months to get proper A5 prints using my 'hp psc 2410 photosmart all-in-one'. And finally and surprisingly it started to work! But now trying to get back to A4 seems to take much more effort. The only thing that I have found out so far is that in Finnish language there are multiple excellent and very strong synonyms for translation of word frustration. - And still, I'm seriously suggesting people to switch over and start to use UBUNTU.

Say no more...






> **nixi said:**
> I have been trying to control printing on paper sizes such as A3, A2, and A1 on an Epson Stylus Pro 7500, and I'm sorry to say it seems close to futile in Ubuntu. Yet I did manage to print a couple of A1 sized documents by doing this: 

1. deleted and reinstalled the recommended printer driver 
2. entered CUPS gui by [http://localhost:631](http://localhost:631), and set "media size" to "A1"
3. sudo gedit /etc/cups/ppd/printer's-name.ppd, and set StpDefaultPageSize, StpDefaultPageRegion, StpDefaultImageableArea, and StpDefaultPaperDimension to "A1" (they were still "letter" in spite of CUPS)
4. sudo dpkg-reconfigure libpaper1, and selected "A1" (to set /etc/papersize to "a1")
5. opened the documents (pdf) in Evince, selected "A1" from printer properties, and printed them.

So evidently it is possible to print A1 sized documents. However, I also have a standard sized laser printer, and I wanted to print some ordinary A4s. Therefore I typed sudo dpkg-reconfigure libpaper1 again, selected "A4" (to set /etc/papersize to "a4"), selected the laser printer, and managed to print A4 sized documents. 

Later, when I wanted to print those A1 sized documents on the Epson again, I typed sudo dpkg-reconfigure libpaper1, selected "A1", and started the printing.  But this time the document was cropped, as if the system was stuck on "letter", and seemingly indifferent to all the above mentioned settings being set to "A1". I have done the entire procedure from 1 to 5 again, restarted printer, computer, reset power, but the system keeps on cropping the documents indifferent to any user controlled settings. And this is, of course, extremely frustrating. Especially since I use Ubuntu at work.  

Any constructive advice appreciated, thanks!

---

### Post by nixi on 2009-05-13
Unlike other programs Evince uses the locale setting to determine papersize (which I think is wrong). One solution for changing "letter" to "a4" is to open .profile and add the following line: export LC_PAPER=a4 

For other sizes such as A5 I don't know whether "export LC_PAPER=a5" would work but I'd give it a try. 

I use Gimp for printing my A1 documents, which works well enough for now. Gimp seems to comply to the settings in the proper user interface for printing.

---

### Post by EKa on 2009-05-16
Thanks nixi, updating the ".profile" solved my a4 problem. I will try a5 next.


> **nixi said:**
> Unlike other programs Evince uses the locale setting to determine papersize (which I think is wrong). One solution for changing "letter" to "a4" is to open .profile and add the following line: export LC_PAPER=a4 

For other sizes such as A5 I don't know whether "export LC_PAPER=a5" would work but I'd give it a try. 

I use Gimp for printing my A1 documents, which works well enough for now. Gimp seems to comply to the settings in the proper user interface for printing.

---

