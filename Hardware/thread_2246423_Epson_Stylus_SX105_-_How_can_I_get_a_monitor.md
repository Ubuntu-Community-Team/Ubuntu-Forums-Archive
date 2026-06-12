---
title: "Epson Stylus SX105 - How can I get a monitor?"
date: 2014-09-30
forum: Hardware
---

### Post by hfsb on 2014-09-30
Hi!

I have the printed that I mentioned in the title and in spite of I being able to print and scan without any problems, I can't check the ink level, change the cartridge, and other kind of options that are available using the proper driver in Windows.

There is any kind of monitor for me to manage my printer?

Thanks.

---

### Post by slickymaster on 2014-09-30
There's [mtink in the repos]("http://packages.ubuntu.com/trusty/mtink"). It's a printer status monitor which enables to get the remaining ink quantity, to print test patterns, to reset printer and to clean nozzle and it's target to Epson.

---

### Post by hfsb on 2014-09-30
> **slickymaster said:**
> There's [mtink in the repos]("http://packages.ubuntu.com/trusty/mtink"). It's a printer status monitor which enables to get the remaining ink quantity, to print test patterns, to reset printer and to clean nozzle and it's target to Epson.

Thanks. How can I install this on Lubuntu?

---

### Post by slickymaster on 2014-09-30
Either search for it in the Ubuntu Software Center and install through it or in a terminal window run:```
sudo apt-get install mtink
```

---

### Post by hfsb on 2014-09-30
> **slickymaster said:**
> Either search for it in the Ubuntu Software Center and install through it or in a terminal window run:```
sudo apt-get install mtink
```

Thanks, now it's installed. However, when I launch the application, I get this message:

*No acess to print device file. Please make sure that mtink has enough right for accessing the device files.*

---

### Post by slickymaster on 2014-09-30
As the error message itself says, it's a matter of permissions. Add your user to the group **lp **via "Users and groups" or editing the file **/etc/group** to add your user.

If you opt for editing the file, in a terminal:```
gksu leafpad /etc/group
```will open the file in edit/save mode.

Here's part of my /etc/group file:```
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:username
tty:x:5:
disk:x:6:
**[COLOR=#ff0000]lp:x:7:username[/COLOR]**
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:

...
```

---

### Post by hfsb on 2014-09-30
Now I got this message:

[I]Problems with the printer communication, please check the printer for errors: "Out of Paper", "No Ink", "printer not powered".

Note that some printer block for a few seconds after powering on.[/I]

I checked the erros, and it's everything OK with the printer. When I launch the application I choose the device, and in Printers I have selected "other printers", since Stylus SX105 doesn't appear on the list.

---

### Post by slickymaster on 2014-09-30
It may take a few minutes the first time you launch it, even after adding your user to the lp group, but it should work. You may even need to reboot before the system picks up the change.

---

### Post by hfsb on 2014-10-01
I still get the error :(

---

### Post by slickymaster on 2014-10-01
It could be that cups doesn't use usblp module anymore and mtink might need it. You can load that module manually, then use mtink. However, you'll have to remove usblp afterwards:```
sudo modprobe usblp
sudo mtink
sudo modprobe -r usblp
```If this works for you, and to make sure you don't forget to load/unload the usblp module, you can add the following function to your .bash_aliases file, so that simply typing mtink command loads the module, executes mtink, and then module is unloaded```
function mtink() {
   sudo modprobe usblp
   sudo mtink
   sudo modprobe -r usblp
}
```

---

### Post by hfsb on 2014-10-01
When I type sudo modprobe usblp and then sudo mtink, the application opens and the printer reacts like a printing, however the paper doesnt come out.

In the terminal, I get this: 

*Warning: Cannot convert string "*-helvetica-*-r-normal--14-*-*-*-*-*-iso8859-1" to type FontStruct*
*Warning: Cannot convert string "*-helvetica-medium-r-normal-*-12-*-*-*-*-*-iso8859-1" to type FontStruct*
*Unable to begin conversation, try later.*
*Unable to begin conversation, try later.*

And then it shows the same error as I told above:

*Problems with the printer communication, please check the printer for errors: "Out of Paper", "No Ink", "printer not powered".*
[I]
Note that some printer block for a few seconds after powering on.
[/I]

---

### Post by slickymaster on 2014-10-02
> **hfsb said:**
> When I type sudo modprobe usblp and then sudo mtink, the application opens and the printer reacts like a printing, however the paper doesnt come out.

In the terminal, I get this: 

*Warning: Cannot convert string "*-helvetica-*-r-normal--14-*-*-*-*-*-iso8859-1" to type FontStruct*
*Warning: Cannot convert string "*-helvetica-medium-r-normal-*-12-*-*-*-*-*-iso8859-1" to type FontStruct*
*Unable to begin conversation, try later.*
*Unable to begin conversation, try later.*

And then it shows the same error as I told above:

*Problems with the printer communication, please check the printer for errors: "Out of Paper", "No Ink", "printer not powered".*
[I]
Note that some printer block for a few seconds after powering on.
[/I]

Looks like you don't have some of the fonts installed. Do you have the package ttf-mscorefonts-installer in your system? If not install it:```
sudo apt-get install ttf-mscorefonts-installer
```and then try again to run```
sudo modprobe usblp
sudo mtink
sudo modprobe -r usblp
```

---

### Post by hfsb on 2014-10-02
I already have the package ttf-mscorefonts-installer.

I did what you asked and I get this in the terminal:

Warning: Cannot convert string "*-helvetica-*-r-normal--14-*-*-*-*-*-iso8859-1" to type FontStruct
Warning: Cannot convert string "*-helvetica-medium-r-normal-*-12-*-*-*-*-*-iso8859-1" to type FontStruct
Unknown IEEE 1284.4 error number 66

---

### Post by slickymaster on 2014-10-03
I must confess that for a simple printer monitor it's not worth all the time and trouble you've been having so far. And I also confess that I can't make heads or tails of the why of all the errors.

In any case I think there's another solution you can try. [**escputil**]("http://www.linuxcommand.org/man_pages/escputil1.html") is a command line utility to perform various maintenance tasks on Epson Stylus inkjet printers.  These tasks include head alignment, head cleaning, nozzle check, printer identification, and retrieval of ink level from the printer. To install:```
sudo apt-get install escputil
```

In addition to it, you have [Stylus Toolbox]("http://stylus-toolbox.sourceforge.net/index.html"), a graphical (GUI) front-end for Gutenprint's escputil command-line Epson printer utility.

---

