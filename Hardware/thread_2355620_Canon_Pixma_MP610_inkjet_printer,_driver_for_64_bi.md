---
title: "Canon Pixma MP610 inkjet printer, driver for 64 bit Buntu 16.04"
date: 2017-03-14
forum: Hardware
---

### Post by mörgæs on 2017-03-14
Has anyone managed to get the printer working under a 64 bit Buntu 16.04? 

Canon offers only 32 bit drivers for download from their web site. The latest I was able to find was from 2009 (so the next printer will be a Brother).

The PPA's 
```
ppa:michael-gruz/canon-trunk
ppa:michael-gruz/canon 
ppa:inameiname/stable
```

which I have used earlier contain a fine selection of drivers but they are also 32 bit and/or for older releases than 16.04. I even [posted]("https://ubuntuforums.org/showthread.php?t=361236&page=87&p=12909495&viewfull=1#post12909495") about using the PPA's once but now they don't seem to be an option.

Does anyone have a suggestion for where to go next? 
Advice for other Pixma MP's is also received with gratitude.

---

### Post by pdc on 2017-03-14
we don't have such a printer but I did save some links where folks used symbolic links if they were using a 64bit system for Canon (UFR) drivers . and the drivers were seen as 32bit; [https://ubuntuforums.org/showthread.php?t=2021854](https://ubuntuforums.org/showthread.php?t=2021854)

they were ```
sudo ln -s /usr/lib /usr/lib64
sudo ln -s /usr/local/lib /usr/local/lib64
```

I wonder if they would still be applicable. Brother have long recommended the format that you will know of ```
 dpkg  -i  --force-all  (lpr-drivername)
``` and I wonder if that be appropriate for the 32bit drivers for your MP610. The drivers from Canon that they hold are I see from 2007 and in the format of that era where the common is installed first, then the specific driver. Credit to yourself and Canon that a 10 yr old printer still goes well. 

[http://search-asia.canon-asia.com/canon__asia_en__asia_p_en/search.x?q=&ie=utf8&cat=0&ct=Support&pagemax=10&imgsize=1&pdf=ok&zoom=1&hf=category%09zubaken&cf=model_sm%3APIXMA+MP610&modelName=PIXMA+MP610&ref=support-asia.canon-asia.com&pid=iPpTU8W8QRsfSIOPWv0Jqg..&qid=Q5pyz2wA9UOSF55Yi4q1iN-B52mgXtus&d=DOWNLOADS%09Linux](http://search-asia.canon-asia.com/canon__asia_en__asia_p_en/search.x?q=&ie=utf8&cat=0&ct=Support&pagemax=10&imgsize=1&pdf=ok&zoom=1&hf=category%09zubaken&cf=model_sm%3APIXMA+MP610&modelName=PIXMA+MP610&ref=support-asia.canon-asia.com&pid=iPpTU8W8QRsfSIOPWv0Jqg..&qid=Q5pyz2wA9UOSF55Yi4q1iN-B52mgXtus&d=DOWNLOADS%09Linux)

I see Turboprint do not support the MP610; and gutenprint describe their support as experimental; [http://gimp-print.sourceforge.net/p_Supported_Printers.php](http://gimp-print.sourceforge.net/p_Supported_Printers.php)  ......not sure if that is false modesty or a true state;

____________

```
Advice for other Pixma MP's is also received with gratitude. 
```     .... I wasn't sure what this meant: did you quietly want us to recommend to you that you deserve a brand new printer, and tell you are worth it; so just go out and buy it?

---

### Post by mörgæs on 2017-03-15
Hi, thanks for your reply.

> **pdc said:**
> 
```
Advice for other Pixma MP's is also received with gratitude. 
```     .... I wasn't sure what this meant: did you quietly want us to recommend to you that you deserve a brand new printer, and tell you are worth it; so just go out and buy it?

It means that I expect a driver for any of the MP6xx printers to be (at least partially) useful. I am certainly not going to buy from Canon and I hope that I don't have to buy a printer at all - I like to keep old stuff functional.

Yes, I also noticed the [UFR drivers]("https://wiki.debian.org/PrinterDriver/Canon/UFR-II#Printers_Supporting_Canon_UFR_II.2FUFR_II_LT") but since the page linked to does not mention the MP6xx class of printers I have not proceeded further. Anyone tried installing them?

---

### Post by mörgæs on 2017-05-25
Now I found a solution. Your post pointed me in the right direction to use the 32 bit drivers.

First do the normal ```
sudo apt update 
sudo apt dist-upgrade
```
to begin with a stable system. 

After that the following two commands 
```
sudo dpkg --force-architecture -i cnijfilter-common_3.20-1_i386.deb 
sudo dpkg --force-architecture -i cnijfilter-mp6XXseries_3.20-1_i386.deb

```do the trick. XX indicates the number of the printer, in this case 10 but I expect the solution to work for others, too.

If something goes awry then ```
sudo apt-get -f install
``` solves the problem. No PPA's needed.

---

### Post by pdc on 2017-05-25
thanks for your news; glad to hear it is all working;

---

