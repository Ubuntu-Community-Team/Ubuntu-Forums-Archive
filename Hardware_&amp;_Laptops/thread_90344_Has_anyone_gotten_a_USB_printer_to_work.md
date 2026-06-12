---
title: "Has anyone gotten a USB printer to work?"
date: 2005-11-14
forum: Hardware &amp; Laptops
---

### Post by discofro on 2005-11-14
I am having the exact same error as many other people on this forum, specifically when I select System->Administration->Printing->Add Printer, the program 'gnome-cups-add' immediately fails and crashes and will not run. 

I used this same procedure on another computer using ubuntu and it worked immediately (however, this was a parellel port printer NOT a USB printer)

I checked every forum listing and it seems like all the posts just stop with no conclusive 'This is how to fix it' answer. The Ubuntu wiki is also seemingly empty on this problem.

So my question is... is there a fix or is my printer just an expensive paperweight?

Thanks

---

### Post by darknuala on 2005-11-14
What model printer are you using?  I have used both USB and Parallel and haven't had a problem with either.

---

### Post by discofro on 2005-11-14
I am trying to use an Epson Stylus C60. It's fairly old (2001). I tried it out in Windows and windows found it instantly and was able to print from it, so I know my printer itself is ok. 

But if you do a search on the forums for 'gnome-cups-add' you will find about 10 other posts all with exactly the same error. Which leads me to believe that perhaps someone has a solution to this...

any ideas?

---

### Post by cclemon on 2005-11-15
I'm getting the same error while adding a new printer. 

When I "sudo gnome-cups-add" from the terminal, I get loads of errors, like this:

> 
** (gnome-cups-add:8742): WARNING **: Two ppds have driver == 'hpijs (recommended)'
        ->hplip/HP-PSC_2400-hpijs.ppd (HP PSC 2400 Foomatic/hpijs[1]) and
        ->foomatic-ppds/hplip/HP-PSC_2400-hpijs.ppd (HP PSC 2400 Foomatic/hpijs)[1]


Any solution for this problem?

---

### Post by cclemon on 2005-11-15
I managed to install a printer by using the CUPS web interface following this 
[post]("http://www.ubuntuforums.org/showthread.php?t=84037&highlight=gnome-cups-add")

---

### Post by discofro on 2005-11-15
On the web portal interface... this appears at the top of my screen

Administrative tasks have been disabled for security reasons. Please use Menu System > Administration > Printing.

But of course this doesn't work as this is what causes the error in the first place... how can I change this setting?

I guess secondly, this portal also asks for my user name and password. I give it, but it refuses. I only have one account on this machine... what does it want? I thought ubuntu couldn't have a root user...

---

### Post by cmlal on 2005-11-15
I'm having the same problem. I was just going to ask about what kind of username and password it is asking for. I am so puzzled by all this...

---

### Post by cmlal on 2005-11-15
Ok, so I've been through now this with some help from LQ. [Here is the thread.]("http://www.linuxquestions.org/questions/showthread.php?s=&threadid=383371&perpage=15&pagenumber=1") I managed to sort of log in (by removing the username and password prompt) and I managed to get my printer detected (as two devices actually...) but the problem remains.

Please have a look at the end of the mentioned thread and see if you have any suggestions. Thank you so much! (I hope it is ok to refer to other forum threads on here, it's easier than rephrasing them.)

---

### Post by cclemon on 2005-11-18
I managed to install the printer through the web-interface by using my user and password. But maybe it works with the root password...

To change the root password:

```
sudo passwd root
```

Then type the password of your choice then confirm the password.

When te web-interface asks you for the user and password, use "root" and the password you choosed above.

---

