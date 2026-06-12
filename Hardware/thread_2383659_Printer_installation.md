---
title: "Printer installation"
date: 2018-01-28
forum: Hardware
---

### Post by leett64 on 2018-01-28
Hi 
I am new to Linux and have just installed Ubuntu 16.04 on my vaio laptop and I am having trouble with my brother hl1112 printer.
I plugged it in and installed the recommended files but the exact printer was not there, when I did a test page the printer took in a sheet of paper and just passed it straight through without anything printed on the paper.
I went to the brother site and just confused myself with the instructions given.
Thanks in advance Lee

---

### Post by pdc on 2018-01-28
Hi Lee;

welcome to the Ubuntu forums; we hope you enjoy Ubuntu

Brother provide an installer tool so it should do most of the work for you; if you go here [http://support.brother.com/g/b/downloadhowto.aspx?c=us_ot&lang=en&prod=hl1112_us_eu&os=128&dlid=dlf006893_000&flang=4&type3=625](http://support.brother.com/g/b/downloadhowto.aspx?c=us_ot&lang=en&prod=hl1112_us_eu&os=128&dlid=dlf006893_000&flang=4&type3=625) and click to download and SAVE what will be [COLOR="#0000FF"]linux-brprinter-installer-2.2.0-1.gz[/COLOR]

then you need to open a terminal: ............ hold down three keys; the control and the alt and the t keys .......... then you need to copy the commands below; and paste them into the terminal; control and v are the buttons normally to paste; in the terminal it is three: control and shift and v  .. or else right-click at the text prompt in the terminal ... the flashing light ............ and look for PaSTE in the menu that appears when you right-click there ..........

```
cd Downloads
```

```
gunzip linux-brprinter-installer-2.2.0-1.gz
```

```
sudo bash linux-brprinter-installer-2.2.0-1 HL-1112
```

we hope it all goes well;

---

### Post by leett64 on 2018-01-28
Thanks for the response I will try that tomorrow and let you know if it worked and I do like what I have seen so far and I am looking forward to getting more involved with Ubuntu

---

### Post by VMC on 2018-01-28
Also, read this post:
[https://ubuntuforums.org/showthread.php?t=2382925&p=13731826#post13731826](https://ubuntuforums.org/showthread.php?t=2382925&p=13731826#post13731826)

---

### Post by leett64 on 2018-01-29
just installed the printer and somehow i had already downloaded the installer but didn't know how to run it, i followed your directions and i now have my printer working perfectly.
thanks for the fast help, i think i need to learn how to use the terminal correctly to get the most out of ubuntu

---

### Post by pdc on 2018-01-29
that's great; enjoy linux; 

>  i think i need to learn how to use the terminal  ........ often just being good at COPY and PASTE is the answer!! .......... increasingly, so much can be GUI on Ubuntu these days


....... oh; and as it is your thread; if you go to THREAD TOOLS at the top; you can add SOLVED ...... then anyone following can find what worked for you

---

### Post by _fragus on 2018-03-04
Thank you very much for this thread. It helps me solve my printing problem.
You guys are great!

---

