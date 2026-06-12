---
title: "Where Is My &quot;kernel&quot;"
date: 2005-11-06
forum: General Help
---

### Post by bsbture on 2005-11-06
hello all~!this is my first time to use GNU/LINUX (so i have dual systems ),and i have chosen breezy to run on my IBM T43.Nevertheless,i confront some questions nowadays:
1.where is kernel located in ubuntu?
2.how can i edit or recompile the kernel that I am using now?


I am from R.P CHINA,thus my english is not so good ,sometimes I cannot express what I want to say appropriately.  ^_^


THANK YOU FOR YOUR HELP

---

### Post by 23meg on 2005-11-06
Hello and welcome. You can refer to [this thread]("http://www.ubuntuforums.org/showthread.php?t=85064") for compiling your own kernel.

---

### Post by nightfly on 2005-11-06
> 1.where is kernel located in ubuntu?
The kernel is located at /boot :) 

> 2.how can i edit or recompile the kernel that I am using now?

I would like to inquire on why you are interested in recompiling the kernel at this early stage ? Contrary to what new users might think, recompiling the kernel does not change the appearance of your desktop or the general functions. It does not make your desktop "fancier" by any means.

---

### Post by bsbture on 2005-11-06
[QUOTE=nightfly]The kernel is located at /boot :) 


I would like to inquire on why you are interested in recompiling the kernel at this early stage ? Contrary to what new users might think, recompiling the kernel does not change the appearance of your desktop or the general functions. It does not make your desktop "fancier" by any means.[/QUOTE]
uh ...surely I know that it does not help me improve the appearance of my desktop,but the only thing I wanna do is to compile some infrared kernel modules ,in order to link my mobile phone.
so ,anyone can tell me how can I achieve this purpose avoiding to compile my kernel?

---

### Post by Xian on 2005-11-06
[QUOTE=bsbture]the only thing I wanna do is to compile some infrared kernel modules ,in order to link my mobile phone.
so ,anyone can tell me how can I achieve this purpose avoiding to compile my kernel?[/QUOTE]
If you want to compile new modules into your kernel you'll need to make a new one from source.  The link to the forum thread that was given is a good place to start.

---

### Post by 23meg on 2005-11-06
Take a look at [this page]("http://linux.spiney.org/book/print/71"); the author says he needed to patch his kernel for infrared to work in Debian. The computer in question seems to be a T43P though; I don't know what difference there is but if yours doesn't have the P it may have a different infrared device as well.

Can you please check if the device is detected in Device Manager and tell us its exact name if it is?

---

### Post by bsbture on 2005-11-07
I think both T43 and T43p have the same ifrared device.
now ,I could not find the name of it under ubuntu, but under windows ,it is named "ibm thinkpad fast infraed device "

---

### Post by 23meg on 2005-11-07
If it's the same device the instructions on that page should apply to Ubuntu as well; give them a try.

---

### Post by bsbture on 2005-11-23
oh ,i was preparing for my TOEFL last two weeks .it is so boring.now i am back to my linux

---

