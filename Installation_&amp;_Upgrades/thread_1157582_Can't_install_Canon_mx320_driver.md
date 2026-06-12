---
title: "Can't install Canon mx320 driver"
date: 2009-05-12
forum: Installation &amp; Upgrades
---

### Post by MacBear on 2009-05-12
I have recently installed 9.04 on a Compaq Presario AMD 64 machine that is dual booted with VISTA. The seniors volunteer group I do computer support for has a Canon Pixma MX320 which I found drivers at Canon Europe. My problem is that I don't know how to proceed with installation of the drivers. Oh, and the printer is connected by usb.  If anyone can be of help I would greatly appreciate it.

---

### Post by ikarustigger on 2009-11-19
> **MacBear said:**
> I have recently installed 9.04 on a Compaq Presario AMD 64 machine that is dual booted with VISTA. The seniors volunteer group I do computer support for has a Canon Pixma MX320 which I found drivers at Canon Europe. My problem is that I don't know how to proceed with installation of the drivers. Oh, and the printer is connected by usb.  If anyone can be of help I would greatly appreciate it.

Had a similar Problem and solved it like this:
0.) Download Driver from [http://software.canon-europe.com/software/0033553.asp?model=](http://software.canon-europe.com/software/0033553.asp?model=)
(link at bottom left of page)
1.) Install cnijfilter-common_3.10-1_i386.deb and cnijfilter-mx320series_3.10-1_i386.deb included in cnijfilter-mx320series-3.10-1-i386-deb.tar.gz from the Canon Support page.
2.) Go for System -> Administration -> Printing
and select "New" - select the connection-type to the printer - if connected via USB it should detect it automatically - mine came shared from some Windows box (URI: smb://SHARE/HOMEPC/Drucker2 ).
3.) At the driver Selection select "PPD-File", click on the folder-box below  and give it the following path: /usr/share/ppd/canonmx320.ppd
4.) Click "Next" and "Apply" - and print a test page
- Done -.

Hope it works for you too !

---

### Post by Jason Argonaut on 2010-05-13
ikarustigger says: 
[B]
          1.) Install cnijfilter-common_3.10-1_i386.deb and cnijfilter-mx320series_3.10-1_i386.deb included in cnijfilter-mx320series-3.10-1-i386-deb.tar.gz from the Canon Support page.[/B]

How do you do that?

sh doesn't do the trick.

---

### Post by manu7irl on 2010-05-14
That did the trick for me on Ubuntu 10.04 64 bit!
Simply run in terminal from the folder where you placed the 2 packages :

```
sudo dpkg -i --force-architecture ./cnijfilter-common_3.10-1_i386.deb
```

and then :

```
sudo dpkg -i --force-architecture ./cnijfilter-mx320series_3.10-1_i386.deb
```





Emmanuel.

Pc configuration :
motherboard : gigabyte GA-MA785G-UD3H
processor : AMD Athlon II quad core 630 2.80Ghz
memory : 2 x 2 Gb DDR2 800Mhz
video card : onboard ATI HD4200
OS : dualboot grub2 Ubuntu 10.04 64bits / Windows 7 32 bits

---

### Post by manu7irl on 2010-05-14
I think that the person who opened this topic can put the [RESOLVED] thing on top of it!

---

### Post by andyb132 on 2011-03-15
No, it does not work.  This misleading post should be removed.

---

### Post by hmazuji on 2012-04-16
it doesn't work because you may have a 64 bit operating system, and the pixma drivers are 32 bit.

you can figure out what type of operating system you have using:
uname

to overcome this problem where synaptic package manager doesn't want to install 32 bit drivers, you have to use the source code and build your own.

use this as a template to using source:
[http://www.webmonkey.com/2010/02/compile_software_from_source_code/#disqus_thread](http://www.webmonkey.com/2010/02/compile_software_from_source_code/#disqus_thread)

for the pixma mx320, i found the source code here:
[http://www.canon.co.uk/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MX_series/PIXMA_MX320.aspx?DLtcmuri=tcm:14-731997&page=1&type=download](http://www.canon.co.uk/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MX_series/PIXMA_MX320.aspx?DLtcmuri=tcm:14-731997&page=1&type=download)

i downloaded and installed gcc and g++ using synaptic package manager.

tar xzvf cnijfilter-source-3.10-1.tar.gz

cd cnijfilter-source-3.10

this is where i am stuck. can't continue with the directions because
root@debian:/home/lou/Downloads/cnijfilter-source-3.10# ./configure
comes back with:
bash: make: command not found

as with
root@debian:/home/lou/Downloads/cnijfilter-source-3.10# make
bash: make: command not found

i couldn't continue on with the installation.

what do i do now ?
(beside run a futile search on google for "bash: make: command not found")

i have the feeling that this is a gnome problem or that i'm using the wrong shell.

do i need to configure or make ?
[ixtok]("http://ubuntuforums.org/member.php?u=43882") suggested:
I typed "dir" to list the files in that directory, it listed a file  install.sh

I typed sudo ./install.sh

The terminal took over and installed everything, asked a couple of questions and the printer works.

i haven't given that a go yet.  i'll let you know.

---

