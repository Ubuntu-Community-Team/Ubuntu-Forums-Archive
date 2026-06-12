---
title: "i have a problem with my scanner"
date: 2008-08-30
forum: General Help
---

### Post by awsi21 on 2008-08-30
Hello there,

I have Genx smart scanner 1200 600dpi, I want to use it on Ubuntu 8.04 and kernel version is 2.6.24-19-generic
I made activation for xsane and when i plugged it some error appeared, which is displayed in the following screen shot:

[IMG]http://www.mriraq.com/vb/imagehosting/248b9b4a5bc308.png[/IMG]


and then I went to terminal and typed:

```
Me:~$ sudo xsane
[sudo] password for Me:
[gt68xx] Couldn't open firmware file (`/usr/share/sane/gt68xx/cism216.fw'): No such file or directory
```

and the same error above appeared again
by the way I am a new user in this OS :guitar:

thanks for all

---

### Post by jonian_g on 2008-08-30
You can try with other scaning software to se if it is xsane's fault. Go to Applications>Add/Remove and you will find an alternative scaning software.

---

### Post by markharding557 on 2008-08-30
have you installed adriver for it quite often you do

---

### Post by awsi21 on 2008-08-31
well thank 4 ur replay 
i don't installing any think couse i don't have it's software on Ubuntu
but i have its CD with exe. 
only program that i installed was xsane and scanner utility and the same problem was appeared 

any one can help me 
i need the scanner so much
regards

---

### Post by awsi21 on 2008-08-31
up up up:confused:

---

### Post by kaibob on 2008-09-01
Your scanner is not shown as supported by sane, although it may work as some other manufacturer/model.

[http://www.sane-project.org/cgi-bin/driver.pl](http://www.sane-project.org/cgi-bin/driver.pl)

Is the needed firmware on your hard drive? What firmware does the snapscan.conf file show? Perhaps you just need to copy the firmware file to you hard drive.

---

### Post by awsi21 on 2008-09-01
thanks 
i do what u told me and i found this file :guitar:
that i attached it to c what firmware should i add
and thanks 4 every thing

pleas im a new user so step by step

---

### Post by awsi21 on 2008-09-01
huh any one can help me

---

### Post by kaibob on 2008-09-01
The first lines of your snapscan.conf file are as follows:

```
# Change to the fully qualified filename of your firmware file, if
# firmware upload is needed by the scanner
firmware /usr/share/sane/snapscan/your-firmwarefile.bin
```

In the final line, you normally need to place the path to your scanner's firmware. That hasn't been done.

I fear that your scanner simply isn't supported, but I don't know enough about configuring scanners to say that with certainty. Perhaps others will be able to help more. Sorry!

---

### Post by awsi21 on 2008-09-01
> **kaibob said:**
> The first lines of your snapscan.conf file are as follows:

```
# Change to the fully qualified filename of your firmware file, if
# firmware upload is needed by the scanner
firmware /usr/share/sane/snapscan/your-firmwarefile.bin
```

In the final line, you normally need to place the path to your scanner's firmware. That hasn't been done.

I fear that your scanner simply isn't supported, but I don't know enough about configuring scanners to say that with certainty. Perhaps others will be able to help more. Sorry!

thank u 
so whats ur suggestion ?

---

### Post by kaibob on 2008-09-02
Sane apparently doesn't support your scanner, so there nothing you can do to get the scanner working under linux--at least as far as I know. 

[http://www.sane-project.org/sane-mfgs.html](http://www.sane-project.org/sane-mfgs.html)

I checked and found that the genx is a very inexpensive scanner. So, rather than spending a lot of time to get it working, you may want to get an inexpensive HP or Epson scanner that is fully supported. I know that's not the answer you want, but in the long run you may be better off. 

If you still want to work with the genx, have a look at post 2 in the following thread:

[http://ubuntuforums.org/showthread.php?t=906762](http://ubuntuforums.org/showthread.php?t=906762)

Sorry I can't be of more help.

---

