---
title: "Canon iP2700 driver installation failure- dependency issues"
date: 2011-04-22
forum: Hardware
---

### Post by a_posse_ad_esse on 2011-04-22
This post was originally tacked onto [this]("http://ubuntuforums.org/showthread.php?t=1556831") thread, but has been moved here as it is identified as a distinct issue.

I was successful in installing the Canon-provide drivers for my iP2700 using the --force-architecture option as described in the above link and other tutorials in Maverick, but now get the following when attempting the same method in Natty:

```

dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 153847 files and directories currently installed.)
Preparing to replace cnijfilter-common:i386 3.30-1 (using cnijfilter-common_3.30-1_i386.deb) ...
Unpacking replacement cnijfilter-common:i386 ...
dpkg: dependency problems prevent configuration of cnijfilter-common:i386:
 cnijfilter-common:i386 depends on libc6 (>= 2.3.4-1).
 cnijfilter-common:i386 depends on libcupsys2 (>= 1.2.1) | libcups2.
 cnijfilter-common:i386 depends on libpopt0 (>= 1.7).
dpkg: error processing cnijfilter-common:i386 (--install):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 cnijfilter-common:i386

```

A check of these failed dependencies has them listed as being installed and fully upgraded.  Is there a workaround for this issue?  Thanks

---

### Post by a_posse_ad_esse on 2011-04-25
Apologies, but *bump.*

---

### Post by Helloyou on 2011-04-28
I'm facing the same problem. In maverick it was running fine. But, I am already in love with unity, so i don't want to rollback again!!!

---

### Post by chris_gs on 2011-04-29
I have the same problem with the MX860 drivers.. and I agree, the new features in 11.04 have me hooked!  But I do need to get the printer going again, any ideas?

---

### Post by Statik on 2011-04-29
I to have the same trouble.

Statik

---

### Post by phoenix122 on 2011-04-29
I'm getting the same problems. For now, I'm using a Windows VM to print but i hope this gets fixed. I'm just starting to get used to natty :-)

---

### Post by Helloyou on 2011-04-30
The way how I managed to print--

After connecting your printer go to System-->Administration-->Printing and install what they recommend or what matches best to your printer
Search, download and install cnijfilter-common_3.40-1ubuntu13_amd64.deb
It will need ia32-libs installed.
After this open a document and press ctrl+p and click print. :p

---

### Post by GhostRaider555 on 2011-05-10
OTRA SOLUCION - ANOTHER SOLUTION -OTRA SOLUCION - ANOTHER SOLUTION


Español------------------
Aqui les traigo un aporte, sucede que los controladores para la CanoniP2700 usan dependencias ya viejas para estos tiempos, así que pueden hacer funcionar su querida impresora quitándole las referencias a las dependencias viejas

....eso fue lo que hice, les dejo un enlace para que puedan descargar el archivo con el trabajo ya hecho, solo es de seguir las intrucciones que vienen y podrán estar imprimiendo tan bien como antes

[https://rapidshare.com/files/461823836/Canon_iP2700_sin_dependencias.zip](https://rapidshare.com/files/461823836/Canon_iP2700_sin_dependencias.zip)

Mejor si lo suben a otros lugares por si algún día se cae el enlace, porque casi no me mantengo por aquí como para arreglarlo. Buena suerte



_________________________________________________________________________


English--------------
Here is a contribution, it happens that CanoniP2700 drivers dependencies are old for these times, so you can run your beloved printer by removing the references to the old dependencies

.... that's what I did, I leave a link so you can download the file with the work already done, only follow the instructions that come and your can be printing well as before

[https://rapidshare.com/files/461823836/Canon_iP2700_sin_dependencias.zip](https://rapidshare.com/files/461823836/Canon_iP2700_sin_dependencias.zip)

Better if you upload it to other places, if the link stops working, because I sometimes I'm here to fix it. Buena suerte

---

### Post by a_posse_ad_esse on 2011-05-16
GhostRaider555, your solution works perfectly.  Thank you very much for this!  I will contact Canon's IT support to inform them that a workaround has been found and hopefully they can adopt this and update the drivers on their end.

---

### Post by Corvair on 2011-06-04
I have the same problem with a new Canon IP2700.
It indicates that it printed the test page but nothing happened.
I wish I could follow your suggesting but it is a bit too complicated for me.

---

### Post by Corvair on 2011-06-04
Helloyou,

Where do you download  cnijfilter-common_3.40-1ubuntu13_amd64.deb from?

Can you help?

Thanks in advance

---

### Post by demonipuch on 2011-06-05
> **Corvair said:**
> Helloyou,

Where do you download  cnijfilter-common_3.40-1ubuntu13_amd64.deb from?

Can you help?

Thanks in advance

Hello

You should add [this ppa]("https://launchpad.net/%7Emichael-gruz/+archive/canon") to your source list. It provides drivers for many Canon PIXMA printer.

 ```

sudo add-apt-repository ppa:michael-gruz/canon
sudo apt-get update
sudo apt-get install cnijfilter-common cnijfilter-ip2700series
```Add your printer and you're done.
You can try to print a test page

---

### Post by Corvair on 2011-06-05
Thank you Demonipuch for your reply

here is the message I get when trying to go to ppa

claude@claude-desktop:~$ sudo add-apt-repository ppa://michael-gruz/canon
Error reading [https://launchpad.net/api/1.0/~/+archive/:](https://launchpad.net/api/1.0/~/+archive/:) HTTP Error 404: Not Found

Can you tell me why, what is error 404?

---

### Post by Corvair on 2011-06-05
Demonipuch,

Thank you very much, my problem is solved.
I was pasting the information you gave me, that did not work so I went to Micheal's ppa site, entered the information manually and finally got it right.

---

### Post by demonipuch on 2011-06-05
I don't know why.

Try this instead :

Add this line to your /etc/apt/sources.list file :
```
deb http://ppa.launchpad.net/michael-gruz/canon/ubuntu <distribution> main
```Change <distribution> according to your distribution name (lucid, maverick, natty)

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3F7B4A1D
sudo apt-get update
```

---

### Post by nechus on 2011-07-01
Does this printer report ink levels in Ubuntu? Thanks

---

### Post by nechus on 2011-07-02
> **nechus said:**
> Does this printer report ink levels in Ubuntu? Thanks

My own answer: YES. It does.

I used "ink".

Install "ink" with sudo apt-get install ink

Then enter this command
ink -p usb

---

### Post by kamiller42 on 2011-07-07
> **demonipuch said:**
> Hello

You should add [this ppa]("https://launchpad.net/%7Emichael-gruz/+archive/canon") to your source list. It provides drivers for many Canon PIXMA printer.

 ```

sudo add-apt-repository ppa:michael-gruz/canon
sudo apt-get update
sudo apt-get install cnijfilter-common cnijfilter-ip2700series
```Add your printer and you're done.
You can try to print a test page
I have been looking to resolve this issue with my Canon MX870 through a few different solutions. Some involved changing install script files. Another had me editing the deb file and re-creating it.  No other solution worked as well as this one. This one is gold for anyone with Canon printer and looking to install a driver.

Thank you!

---

### Post by Alavez on 2011-08-08
Your solution went perfect, Thank You


> **GhostRaider555 said:**
> OTRA SOLUCION - ANOTHER SOLUTION -OTRA SOLUCION - ANOTHER SOLUTION


Español------------------
Aqui les traigo un aporte, sucede que los controladores para la CanoniP2700 usan dependencias ya viejas para estos tiempos, así que pueden hacer funcionar su querida impresora quitándole las referencias a las dependencias viejas

....eso fue lo que hice, les dejo un enlace para que puedan descargar el archivo con el trabajo ya hecho, solo es de seguir las intrucciones que vienen y podrán estar imprimiendo tan bien como antes

[https://rapidshare.com/files/461823836/Canon_iP2700_sin_dependencias.zip](https://rapidshare.com/files/461823836/Canon_iP2700_sin_dependencias.zip)

Mejor si lo suben a otros lugares por si algún día se cae el enlace, porque casi no me mantengo por aquí como para arreglarlo. Buena suerte



_________________________________________________________________________


English--------------
Here is a contribution, it happens that CanoniP2700 drivers dependencies are old for these times, so you can run your beloved printer by removing the references to the old dependencies

.... that's what I did, I leave a link so you can download the file with the work already done, only follow the instructions that come and your can be printing well as before

[https://rapidshare.com/files/461823836/Canon_iP2700_sin_dependencias.zip](https://rapidshare.com/files/461823836/Canon_iP2700_sin_dependencias.zip)

Better if you upload it to other places, if the link stops working, because I sometimes I'm here to fix it. Buena suerte

---

### Post by rs99cool on 2013-03-06
I think I've followed everything up to here but I'm getting these errors and don't know what to do now...
E: Unable to locate package cnijfilter-common
E: Unable to locate package cnijfilter-ip2700series

Any ideas pleeze?

---

### Post by nielshoogkamer on 2014-01-18
I have the same issue:

E: Unable to locate package cnijfilter-ip2700series

I'm guessing the package is no longer available? Are there any alternatives? I bought the Pixma 2700 specifically so that it would work with Linux and I'm trying to get it working with my new linux only laptop

---

### Post by nielshoogkamer on 2014-01-18
I have the same issue:

E: Unable to locate package cnijfilter-ip2700series

I'm guessing the package is no longer available? Are there any alternatives? I bought the Pixma 2700 specifically so that it would work with Linux and I'm trying to get it working with my new linux only laptop

Ok, I just found the answer on a reply to a page offering the same solutions:

Aditya Mahisa [COLOR=#CCCCCC]•[/COLOR] [2 years ago]("http://www.iheartubuntu.com/2012/02/install-canon-printer-for-ubuntu-linux.html#comment-606162185")

[LIST]
[*][&#8722;]("http://www.iheartubuntu.com/2012/02/install-canon-printer-for-ubuntu-linux.html#")
[*]
[/LIST]
[COLOR=#3F4549][I][FONT=inherit]If you using Ubuntu 12.04 LTS[/FONT]
[FONT=inherit]after "sudo add-apt-repository ppa:michael-gruz/canon"[/FONT]
[FONT=inherit]Please change your Software Sources (Update Manager > Settings...)[/FONT]
[FONT=inherit]On Tab "Other Software"[/FONT]
[FONT=inherit]Edit PPA /michael-gruz/canon/ubuntu[/FONT]
[FONT=inherit]main and main (Source Code)[/FONT]
[FONT=inherit]Change Distribution from "precise" to "oneiric"[/FONT]

[FONT=inherit]After than, you can "sudo apt-get update"[/FONT]

After I did the update I ran the same:

[COLOR=#555555][FONT=consolas]sudo apt-get install cnijfilter-ip2700series

again and it worked. Glad I got it to work, the IP2700 has worked well for me on my old Ubuntu laptop for many years and it's still a good printer. [/FONT][/COLOR][/I]



[/COLOR]

---

