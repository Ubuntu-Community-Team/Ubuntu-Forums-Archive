---
title: "Ubuntu 12.04 , Brother HL-2240D duplex printing"
date: 2014-04-08
forum: Hardware
---

### Post by eightbits2010 on 2014-04-08
I need to replace a failed HP laserjet. The Brother HL-2240D claims to have driver(s). My big draw with using
this printer is duplex printing. Does anyone have any experience(s) using this printer and the duplex operation??

Thanks.

---

### Post by sudodus on 2014-04-09
I have a similar printer, Brother HL-2250DN, and I found linux drivers at the web page of Brother. I could understand the instructions, and after some tweaking I had it working (including duplex printing).

---

### Post by eightbits2010 on 2014-04-09
Thank you sudodus.    Your response gives me the confidence to make the purchase. I think this printer will be a welcome
 addition to using the Ubuntu setup.

---

### Post by eightbits2010 on 2014-04-11
sudodus: I visited the web page as you suggested. I did order the 2240D printer which is scheduled to arrive today. In looking over the instructions found at the Brither web page for HL-2240D installation:
   In the Brother on line instructions step 5:
 bash linux-brprinter-installer-*.*.*-* Brother machine name
 What should be entered for &#8220;Brother machine name&#8221; ?
The web site: [http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=hl2240_us_eu&os=128](http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=hl2240_us_eu&os=128)
The file I downloaded: [I][URL="http://support.brother.com/g/b/downloadend.aspx?c=us&lang=en&prod=hl2240_us_eu&os=128&dlid=dlf006893_000&flang=4&type3=625"]Linux-brprinter-installer

[/URL][/I]There were several other downloads the the same page*, *but the above seemed to be the most appropiate.I think that is where you suggested?

Also, did the duplex printed work automatically or did you have to use manual feed?

Thanks so much for your help. I guess I will find out later today........

I will post a response as soon as I get some results, good or bad.
But, if you can please respond to my question about the name thing.

---

### Post by gifford on 2014-04-11
I have only installed using the CL not a script. But when asked for the name it was always the model of the printer. Such as HL-2240D.

---

### Post by pdc on 2014-04-11
Brother seem to have done a major standardisation on their websites: so the previous links where one could download packages seem to have gone: one now enters the device name and one is guided to the brother installer; so I suspect we will only be able to do this from now on

---

### Post by eightbits2010 on 2014-04-11
gifford: I am not familar with the CL ? I will try out the script that downloaded from the web site. Interesting note, when I attempted to use the phone support line I was informed that Brother offers no phone support for Linux. I wonder if that also
means on line support.
UPDATE: I think CL means command line ? What is the best approach to do it that way?

---

### Post by eightbits2010 on 2014-04-11
pdc: So, you are saying that I will have to use the script? That does seem to be the only thing available. The printer arrived about one hour ago, so I will see how far this gets me.
And thanks to all who helped. I am hoping that I can tag this thread solved in the next day or so.

---

### Post by gifford on 2014-04-11
Yes, command line. I use the terminal and follow the instructions on the Brother site. Yes, the site has changed and makes finding things more difficult. You may have to download the drivers again just to have the site let you view the directions. Unfortunately, as I just now tried, it does not give complete instructions as it used to do. I always use the printer as networked but the instructions appear only for USB install.
Will need to explore the new site more to see if the instructions are hidden someplace else. Too bad, Brother had great instructions and I recommended their printers to any Linux user.

---

### Post by gifford on 2014-04-11
Found the place on the site: [http://support.brother.com/g/s/id/linux/en/index.html?c=us_ot&lang=en&comple=on&redirect=on](http://support.brother.com/g/s/id/linux/en/index.html?c=us_ot&lang=en&comple=on&redirect=on)
Boy, they have made it difficult.

---

### Post by eightbits2010 on 2014-04-11
After experimenting with various install(s) which the one with instructions did not seem to work
 very well, I downloaded the suggested  linux-brprinter-installer-2.0.0-0.gz file from and extracted to get the linux-brprinter-installer-02.0-1script and run that from the command line and it seems to work ok.
 The duplex printing is working and I can enable/disable that.  So, next is to learn how to do envelopes then I will be smiling !
 I think I can mark this as solved and once again thanks for the help to all who offered thier advice. Now, just need to figure out
how to mark this thread <SOLVED>;)

---

### Post by ernstblaauw on 2014-06-01
> **eightbits2010 said:**
> After experimenting with various install(s) which the one with instructions did not seem to work
 very well, I downloaded the suggested  linux-brprinter-installer-2.0.0-0.gz file from and extracted to get the linux-brprinter-installer-02.0-1script and run that from the command line and it seems to work ok.
 The duplex printing is working and I can enable/disable that.  So, next is to learn how to do envelopes then I will be smiling !
 I think I can mark this as solved and once again thanks for the help to all who offered thier advice. Now, just need to figure out
how to mark this thread <SOLVED>;)

Hi eightbits2010, I'm thinking about buying this printer. Are you still running 12.04? And do you have 32- or 64-bit? I want the printer to work on 14.04 64-bit and it needs ia32-libs for that (which is not available, as I remember correctly).

---

### Post by eightbits2010 on 2014-06-01
Yes, using 12.04 on 64 bit hardware. After installing the previous mentioned file it is still working. So far I am satisfied this printer.
I really like the duplex printing.:p

---

