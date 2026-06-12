---
title: "Can't print greyscale HP PageWide 452w"
date: 2017-03-06
forum: Hardware
---

### Post by jjboza on 2017-03-06
Hello

in  ubuntu 12.04 and 16.04 I can't  print  greyscale with a printer HP PageWide 452w although I can choose that option in printer configuration. I've tried with so driver and also after installing HPLIP. In both cases all that I print is printer in colour.

I think there is some error in the configuration properties window, I don't know if someone has been in the same trouble and how I cant mend it (maybe modifying ppd file of the printer?)

 

Anyone can't help me?

Thanks

---

### Post by jjboza on 2017-03-07
Hello

in  ubuntu 12.04 and 16.04 I can't  print  greyscale with a printer HP PageWide 452w although I can choose that option in printer configuration. I've tried with so driver and also after installing HPLIP. In both cases all that I print is printer in colour.

I think there is some error in the configuration properties window, I don't know if someone has been in the same trouble and how I cant mend it (maybe modifying ppd file of the printer?)

 

Anyone can't help me?

Thanks

---

### Post by coffeecat on 2017-03-07
*Threads merged and moved to **Hardware**.*

If you do not get a response after about 12 hours, please bump your thread rather than posting a duplicate. Or perhaps the forum downtime yesterday caused you problems finding your first post. Whichever, this section is a better fit for your problem.

---

### Post by pdc on 2017-03-07
this was the old solution .. [https://harbhag.wordpress.com/2010/07/03/enable-grayscale-printing-in-canon-pixma-mp250-series-on-ubuntu/](https://harbhag.wordpress.com/2010/07/03/enable-grayscale-printing-in-canon-pixma-mp250-series-on-ubuntu/)

I wonder does it still work; please let us know: I enclose a thumbnail from the bottom section of job options in the setup for our printer ..... where one could add CNGrayscale and call it true ....... that is for Canon ..... I wonder if Grayscale itself is fine for an HP

---

### Post by jjboza on 2017-03-08
Thank you for sharing this, but unfortunately with this printer it hasn't worked nor with CNGrayscale nor with Grayscale, I will go on trying to find the option

> **pdc said:**
> this was the old solution .. [https://harbhag.wordpress.com/2010/07/03/enable-grayscale-printing-in-canon-pixma-mp250-series-on-ubuntu/](https://harbhag.wordpress.com/2010/07/03/enable-grayscale-printing-in-canon-pixma-mp250-series-on-ubuntu/)

I wonder does it still work; please let us know: I enclose a thumbnail from the bottom section of job options in the setup for our printer ..... where one could add CNGrayscale and call it true ....... that is for Canon ..... I wonder if Grayscale itself is fine for an HP

---

### Post by pdc on 2017-03-08
very occasionally one gets posts on "grayscale": ....... I confess ...  for me  ... never needed (that I knew of  ..)

some older posts [http://unix.stackexchange.com/questions/68830/how-to-force-lp-from-cups-to-print-in-grayscale](http://unix.stackexchange.com/questions/68830/how-to-force-lp-from-cups-to-print-in-grayscale) .... suggest one needs to convert the image to a grayscale version with GraphicsMagick or ImageMagick ............ the former is in the ubuntu repositories I see 

and the latter comes from here [https://www.imagemagick.org/script/index.php](https://www.imagemagick.org/script/index.php)

is this of any help? Perhaps you could enlighten us a little on the uses of grayscale and then we can be better informed to help in future posts

____________

I guess if I google then these answers emerge: [https://en.wikipedia.org/wiki/Grayscale](https://en.wikipedia.org/wiki/Grayscale) and [http://homepages.inf.ed.ac.uk/rbf/HIPR2/gryimage.htm](http://homepages.inf.ed.ac.uk/rbf/HIPR2/gryimage.htm) so it makes me think using GraphicsMagick or ImageMagick would be ok?

---

### Post by jjboza on 2017-03-10
At last I've got.

I have modified ppd file of the printer to change cups filter to use with my printer 

Now I have two printers, one to print in color mode and another one to print greyscale, in this one I have modified hpps filter (postscript filter) to add PJL commands to print grayscale, 

Thank you

---

### Post by pdc on 2017-03-10
thanks; so it seems to hinge on editing the ppd file;

when I look at a ppd file for our Canon inkjet, I get as in thumbnail ........[COLOR="#0000FF"]DefaultColorSpace: RGB[/COLOR]           .........so sounds like that becomes [COLOR="#008000"]DefaultColorSpace: GrayScale[/COLOR]            

so I am guessing that when you say "Now I have two printers, one to print in color mode and another one to print greyscale, in this one I have modified hpps filter (postscript filter) to add PJL commands to print grayscale, "  you are meaning two printer drivers are set up: one that you know is standard, and the other is modified to GrayScale; and you can identify that one easily ...... if I remember right in CUPS [http://localhost:631/](http://localhost:631/) you can install a new printer and point CUPS to a ppd ....... I think they are normally stored in the folder /usr/share/ppd

thanks for this interesting thread; I will paste a couple of links here that anyone following after may find of use

[https://www.jamf.com/jamf-nation/discussions/19072/force-printers-to-print-in-grayscale](https://www.jamf.com/jamf-nation/discussions/19072/force-printers-to-print-in-grayscale)

[https://www.cups.org/doc/postscript-driver.html](https://www.cups.org/doc/postscript-driver.html)

________

and where the ppd for mine says

```
*DefaultColorModel: rgb
```

I could change that to 

```
*DefaultColorModel: Grayscale
``` and I would have to add a definition in that section

---

### Post by jjboza on 2017-03-15
Thank you for these useful links

yes, the key is to modify my ppd file, but the problem is that different printers accept different commands. What I did is to setup a computer with windows to print grayscale, and I printed to a file, so in the begiining of the file I could read the PJL commands for this printer and use them in ubuntu

---

### Post by pdc on 2017-03-15
thanks very much; "[COLOR="#0000FF"]I could read the PJL commands for this printer and use them in ubuntu[/COLOR]"

.... could you just copy and paste the relevant lines ........ then it is on the forum for anyone in the future to get a sense of what they need to do ...........

---

### Post by jjboza on 2017-03-17
Hello

The commands were:

@PJL SET JOBATTR="Render Type = Discrete V3"
@PJL SET GRAYSCALE=COMPOSITE
@PJL SET RENDERMODE=GRAYSCALE

In ppd file I noticed that cups filter for my printer was a file named hpps, so I copied fille hhps into one named hppsGR and I added in it following lines:

os.write(output_fd, b'@PJL SET JOBATTR="Render Type = Discrete V3"\x0a')
os.write(output_fd, b'@PJL SET GRAYSCALE=COMPOSITE\x0a')
os.write(output_fd, b'@PJL SET RENDERMODE=GRAYSCALE\x0a')

os.write(output_fd, UEL)

greetings

---

### Post by jjboza on 2017-03-17
Ah

I forgot to say that in ppd file I changed the line 

*cupsFilter: "application/vnd.cups-postscript 0 hpps"

for

*cupsFilter: "application/vnd.cups-postscript 0 hppsGR"

---

### Post by pdc on 2017-03-17
thanks very much

---

