---
title: "Brother printer hl-l2302d"
date: 2017-06-25
forum: Hardware
---

### Post by Jack_Shankle on 2017-06-25
This is probably in the wrong place so please excuse me. If you move it I will never
find it.
New printer bought 6-25-2017 and I have managed to print a test page.
It keeps on printing the test page when I try to print a short message
from gmail.
I am writing this from a windows computer. Afraid to try it on the Ubuntu PC
Thanks for any suggestions.

---

### Post by lisati on 2017-06-25
> **Jack_Shankle said:**
> This is probably in the wrong place so please excuse me. If you move it I will never
find it.

A free tip for using the forums: from the Quick Links drop-down menu near the top of the page, you can click on "Find all my posts" and "Find all my threads."

---

### Post by wildmanne39 on 2017-06-25
*Thread moved to **Hardware for a better fit**.*

---

### Post by pdc on 2017-06-25
Hi Jack; I am guessing this is the HL-L2300D ....... would that be correct?

so Brother supply an installer tool; you need to open  a terminal to run it; and you need to paste a couple of commands into the terminal to make things happen ......

1) ...... three keys open a terminal control, alt and t all held down together ....... 2) and paste by right-clicking on the text prompt in the terminal ......... you get a menu ........ see PASTE ?

OK; get the installer tool from here [http://support.brother.com/g/b/downloadend.aspx?c=us&lang=en&prod=hll2300d_us_eu_as&os=128&dlid=dlf006893_000&flang=4&type3=625](http://support.brother.com/g/b/downloadend.aspx?c=us&lang=en&prod=hll2300d_us_eu_as&os=128&dlid=dlf006893_000&flang=4&type3=625) and SAVE it as it comes down and it should end up in the DOWNLOADS folder

so after each command is pasted, hit the Enter key to make things happen .........

```
cd Downloads
```

```
gunzip linux-brprinter-installer-2.1.1-1.gz
```

```
sudo bash linux-brprinter-installer-2.1.1-1 HL-L2300D
```

you will be asked some questions so watch the terminal as things happen ................

---

### Post by Jack_Shankle on 2017-06-26
Thank you for responding and your understanding of my lack of knowledge of Grub and Sudo.
The Brother Laser printer is an hl-l2320d. I have no idea if your previous message will work for this
printer. Guess I am going to have to take it back to Staples. That leaves me not knowing what printer 
to get that will work with Ubuntu-mate 16.04 with all the updates. I know that there is a cups driver
on Ubuntu 16.04 but it doesn't seem to work with this printer. All the printer will do is print a test page.
While I a waiting for your response I will try to do what you suggested in your previous message.
Thank you very much....

---

### Post by pdc on 2017-06-26
so Jack one just specifies the printer one wants in the final command ......... so for a 2320 the command is ```
sudo bash linux-brprinter-installer-2.1.1-1 HL-L2320D
```

---

