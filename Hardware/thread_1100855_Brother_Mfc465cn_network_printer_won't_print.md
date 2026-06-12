---
title: "Brother Mfc465cn network printer won't print"
date: 2009-03-19
forum: Hardware
---

### Post by Ben_neB on 2009-03-19
I'm running Ubuntu 8.10, and I can't seem to get my printer to work. I've gotten it to show up in the CUPS screen at 127.0.0.1:631/printers, and when I give it the command to print something, it's built-in screen briefly says "receiving data", but then it just never does anything else. 

To give you an idea of what I have done, I followed the directions here:

[http://solutions.brother.com/linux/en_us/instruction_prn1a.html](http://solutions.brother.com/linux/en_us/instruction_prn1a.html)

As far as I can tell, I've done everything, but I'm still rather new at this, so I may not have. In any case, I didn't seem to get any errors while I followed those directions, except I had to run the command "mkdir /var/spool/lpd" to fix a "path does not exist" error. 

Also, when I installed the cupswrapper driver, the last line of terminal output says "lpadmin: Unable to copy PPD file!".

But when I entered "sudo dpkg  -l  |  grep  Brother" to test the installation as my first link suggested, it seemed to tell me that everything had gone as planned. 

In any case, I then followed the instructions on how to set it up in the cups web interface. Everything was fine, until it came to the step of selecting my printer model. The MFC465cn is not one of the choices, which is what I assume is causing the lack of functionality. I chose something that seemed to be as close to the one I had as possible, hoping it would work, but no dice.


Anyway, I hope I have provided enough information to indicate my error. If not, I should be able to find out anything else. But bear in mind that I'm a bit of a newbie, so speak slowly and use small words. :P

---

### Post by Ben_neB on 2009-03-19
Here's an update: I tried to do all the steps over again, and I noticed that the installation of the cupswrapper drivers did not go as smoothly as I had thought. Here's the output of the command "sudo dkpg -i --force-architecture . . .etc"

```

(Reading database ... 128890 files and directories currently installed.)
Preparing to replace mfc465cncupswrapper 1.0.1-1 (using mfc465cncupswrapper-1.0.1-1.i386.deb) ...
 * Restarting Common Unix Printing System: cupsd                         [ OK ] 
Unpacking replacement mfc465cncupswrapper ...
Setting up mfc465cncupswrapper (1.0.1-1) ...
/usr/local/Brother/Printer/mfc465cn/cupswrapper/cupswrappermfc465cn: 70: cannot create /usr/share/cups/model/brmfc465cn.ppd: Directory nonexistent
/usr/local/Brother/Printer/mfc465cn/cupswrapper/cupswrappermfc465cn: 274: cannot create /usr/share/cups/model/brmfc465cn.ppd: Directory nonexistent
chmod: cannot access `/usr/share/cups/model/brmfc465cn.ppd': No such file or directory
cp: cannot stat `/usr/share/cups/model/brmfc465cn.ppd': No such file or directory
chmod: cannot access `/usr/share/ppd/brmfc465cn.ppd': No such file or directory
 * Restarting Common Unix Printing System: cupsd                         [ OK ] 
lpadmin: Unable to copy PPD file!

```


Evidently, I need a PPD file, or . . . something else. I don't really understand what the errors mean, other than that I'm missing a directory and/or a PPD file. However, I don't know where to get a PPD file, so I'm still stuck.

Any ideas?




<EDIT> Sucess! I was able to simply use a "mkdir" command to create the missing directory, and the install the cupswrapper driver again, and when I went back to the web interface and through all those steps again, I was able to choose the correct model, and a test page printed perfectly! So, I guess the problem is solved. Thanks anyway, everyone!

---

