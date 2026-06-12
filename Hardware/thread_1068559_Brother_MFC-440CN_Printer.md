---
title: "Brother MFC-440CN Printer"
date: 2009-02-13
forum: Hardware
---

### Post by crunchfighter on 2009-02-13
Trying to get the printer working on 8.10 64 bit.

I have the 2 drivers from the Brother website.  
mfc440cnlpr-1.0.1-1.i386.deb
mfc440cncupswrapper-1.0.1-1.i386.deb

When I try to install them by doubleclicking on them, I get "Error.  Wrong architecture 'i386' "

*******

Once I get these two files installed, I need to do the following:

# For dpkg users:
1. Install lib32stdc++6(Debian) or ia32-libs(Ubuntu)
2. Restart the system
3. Use "--force-architecture" option when you install the drivers.
4. After the driver installation, and if there is "/usr/lib64/filter/", copy the file which name starts with "brlpdwrapper" ( in the "/usr/lib/cups/filter/" ) to "/usr/lib64/cups/filter/".
Or confirm there are symbolic links between "/usr/lib/" and "/usr/lib64/".

How do I install the drivers?
Anyone know where I get lib32stdc++6(Debian) or ia32-libs(Ubuntu)?

References: 
[http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html#142](http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html#142)
[http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html)

Thanks.

---

### Post by crunchfighter on 2009-02-13
OK.  Got it working.  Stand by while I compose my solution post.

---

### Post by crunchfighter on 2009-02-13
There is a great post here on Brother printer setups:
[http://ubuntuforums.org/showthread.php?t=590793&highlight=brother+printer](http://ubuntuforums.org/showthread.php?t=590793&highlight=brother+printer)

Downloaded the two driver files in the first post from the Brother website to my Desktop.
Then I created some directories.  

```
craig@craig-laptop:/var/spool$ sudo mkdir lpd
craig@craig-laptop:/var/spool$ cd lpd
craig@craig-laptop:/var/spool/lpd$ sudo mkdir mfc440cn
craig@craig-laptop:/usr/share/cups$ sudo mkdir model

```

Then I ran the install packages.

```
craig@craig-laptop:/var/spool/lpd/mfc440cn$ sudo dpkg --install --force-architecture /home/craig/Desktop/mfc440cnlpr-1.0.1-1.i386.deb

craig@craig-laptop:/usr/share/cups$ sudo dpkg --install --force-architecture /home/craig/Desktop/mfc440cncupswrapper-1.0.1-1.i386.deb
 
```



The heavy lifting was now done.  I then opened the CUPS administration section in firefox by going to [http://localhost:631](http://localhost:631)

From there, I went to administration, then added the printer.  It found the printer right away with the proper network IP address (it's upstairs).

I then went:
System->Administration->Printing 
found my new printer
right-click 
Properties->Print Test Page.

Miller Time!

---

### Post by crunchfighter on 2009-02-13
The SOLVED selection is not available on THREAD TOOLS.  Any ideas?

---

### Post by plucky on 2009-02-13
> The SOLVED selection is not available on THREAD TOOLS. Any ideas? 


See this [link](http://ubuntuforums.org/showthread.php?t=1044714)


Re Brother drivers,did you look in Synaptic for the drivers?

Next time maybe.  


Good Luck

---

