---
title: "Upgrade to Ubuntu 14.04 lts and printer stopped printing"
date: 2016-01-12
forum: Hardware
---

### Post by michael-piziak on 2016-01-12
Upgrade to Ubuntu 14.04 lts and printer stopped printing

Printer:  Brother HL-2140

Under 12.04 lts, at least I had a printer icon at top of screen, it's not there anymore 

Any help?

I've restarted, rebooted, shut printer on and off, etc....   I'm at my witts end 

?

---

### Post by Bucky Ball on 2016-01-12
Have you installed the printer driver from the Brother Solutions Centre> Downloads site> search for your printer? and then adding a printer and choosing the driver when you get to that part?

There is a Linux/Ubuntu .deb driver available for your printer from the Brother support section. There is also the Driver Install Tool. Use that and it should take care of the driver install for you.

---

### Post by michael-piziak on 2016-01-12
The printer installer is corrupt from the Brother Site.  What a company.

See attached image.

This worked fine under 12.04 lts with no need to install a driver.

Michael

A sidenote:  This printer actually did work for a short time after installing 14.04 lts.  It has a new Brother toner in it.  
Perhaps the printer is simply dying - ?

---

### Post by gifford on 2016-01-12
Don't use the Ubuntu software center to install. Use the command line and you will not have any problems. On the Brother site where you 
get the drivers, they have step by step instructions for installation by the CL.

---

### Post by michael-piziak on 2016-01-13
I need help with what to type into terminal.  The driver automatically downloaded to my download folder.

But in terminal, when I copy and paste what "Brother" wants me to, I get errors in terminal..

The instructions are at: [http://support.brother.com/g/b/downloadhowto.aspx?c=us&lang=en&prod=hl2140_all&os=128&dlid=dlf005857_000&flang=4&type3=559](http://support.brother.com/g/b/downloadhowto.aspx?c=us&lang=en&prod=hl2140_all&os=128&dlid=dlf005857_000&flang=4&type3=559)

My terminal attempt is below and also the instructions are below as a screenshot also.

FYI:  the name of the driver now in my download folder is:  brhl2140lpr-2.0.2-1.i386.deb

---

### Post by Bucky Ball on 2016-01-13
You double click a .deb file and it will open and install using Software Centre. You can also use Gdebi to install it.

Is that the right one for your printer? You only need the [printer driver install tool.]("http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=hl2140_all&os=128") That is the page you should be on for drivers for that device.

---

### Post by michael-piziak on 2016-01-13
We are getting somewhere now.  But not quite there.

This printer driver install tool is:  linux-brprinter-installer-2.0.0-1.gz

When i double click the file I get the below screenshot and it scrolls down forever.

What do I do with this .gz file?

---

### Post by Bucky Ball on 2016-01-13
See [here]("http://support.brother.com/g/b/downloadhowto.aspx?c=us&lang=en&prod=hl2140_all&os=128&dlid=dlf006893_000&flang=4&type3=625").

Replace wherever it says 'linux-brprinter-installer-*.*.*-*.gz' with the details of the driver you downloaded in place of '*.*.*.*'

---

### Post by gifford on 2016-01-14
Where the ( bracket ) is you use the name of the actual driver file, eliminate the brackets.

---

### Post by michael-piziak on 2016-01-14
Please see what I did attached as a screenshot.

What did I type in wrong?  Someone tell me *exactly* what to type into terminal - spoon feed me like a baby.

Michael

---

### Post by gifford on 2016-01-14
Don't use the linux brprinter installer.

Instead, use the command line to install the driver.
Sudo dpkg -i --force-all brhl214lpr-2.0.2-1.i386.deb


Also, if files are in your Downloads folder, just type cd Downloads to change the directory.

---

### Post by michael-piziak on 2016-01-15
ok I will try that

it is in download folder, so I type into terminal "cd" first 

then I type in

Sudo dpkg -i --force-all brhl214lpr-2.0.2-1.i386.deb

right?

It's at my mom's house (her printer) so I will give this a go when I get home.

If I put the file on the desktop, then I can just type  

Sudo dpkg -i --force-all brhl214lpr-2.0.2-1.i386.deb

without the cd part, right?


thanks,

Michael

---

### Post by gifford on 2016-01-15
First cd Downloads to change the directory.
The command listed comes from the Brother site where you downloaded the file from.
Follow the instructions there, just remember when brackets are used, they expect you
to enter your information, i.e, the name of the file, etc.

---

