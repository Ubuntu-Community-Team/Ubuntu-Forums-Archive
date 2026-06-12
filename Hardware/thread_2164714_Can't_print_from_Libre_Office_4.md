---
title: "Can't print from Libre Office 4"
date: 2013-08-01
forum: Hardware
---

### Post by chris-burmajster on 2013-08-01
I wonder if somebody could help me, please? 

Recently I bought a new printer, a Canon Pixma iP7250 which connects 
via wi-fi. I installed it using the supplied Canon drivers for Linux 
and I can print wirelessly without problem from every program in 
Ubuntu except Libre Office. When I try to print a document (either 
existing or new, either a .odt or a .doc) the printer icon shows for 
about 10 seconds and then disappears. Going into ‘view print queue’ 
and looking at the document I just tried to print, it says ‘job 
completed’, but when I press the refresh button it momentarily says 
‘printer not found’. If I save the document as a pdf, it prints fine 
from pdf viewer, but this can only be a temporary workaround. I also 
have the same version of Libre Office on an old Windoze machine 
running XP and I can print from that without any problem, so this must 
be an Ubuntu issue. I am running 13.04. 

I have looked both in the printer settings and the printer settings 
within Libre Office and cannot see anything untoward. In have also 
searched the internet via Duck Duck Go and even, in desperation, used 
Messrs Page & Brin’s search engine, but I could not find anything on 
this particular issue. 

I would be very grateful for any advice on this issue, as I tend to 
print more from Libre Office than any other program. 


Thanks

---

### Post by EBWQNHD on 2013-08-02
the printer admin for Libre Office harks back to the older OpenOffice days

if you issue the command

> [COLOR=#ff0000]/usr/lib/libreoffice/program/spadmin[/COLOR]

it opens the printer administration page............check you really have the ip7250 installed

(you can check with the command 

> [COLOR=#ff0000]sudo dpkg -l | grep cnijfilter[/COLOR]

let us know if any of this helps

---

### Post by Bucky Ball on 2013-08-02
*Thread moved to **Hardware**.*

Welcome to the forums. 

Hmm. I just ran the second command and it returned nothing:

```
sudo dpkg -l | grep cnijfilter
```

My printer is installed and functioning fine in all programs, including LO, so should be there. No typos, syntax fine? 

I would suggest the printer issue is indeed specific to LO, though, rather than being a setting elsewhere, as if a printer driver is installed it should work globally, with all apps. As it appears to be working with all other apps, I'd take it as a given it is installed and functioning. You have proved this conclusively by printing fine otherwise, including PDFs).

---

### Post by Peter Maunder on 2013-08-02
I have sometimes found similar symptoms if there is a missmatch between paper sizes. For example between A4 and Letter. Have you checked the settings in FORMAT>PAGE and that the etc/papersize file is set to the correct size. LibO appears to use the papersize setting whereas many other programs ignore it.  Peter

---

### Post by chris-burmajster on 2013-08-02
Thank you all for your responses. I have checked that the printer is shown in Ubuntu, as it prints from every other program except LO. I have also checked the paper sizes; both are set to A4, in general printer settings and in LO. It has been suggested to me that I should uninstall LO and do a fresh install downloaded directly from LO's website, as apparently, there are differences between the version that comes with Ubuntu and the downloads. I will try this tomorrow unless you think otherwise!

---

### Post by Bucky Ball on 2013-08-02
I imagine 13.04 has the latest. Open LO and Help>About. Check the version number. Go to the site and see what's available. Can't see a reinstall will make much difference, but guess you could try. A similar approach would be to change the name of your LO profile. It will make a new, default, empty one next time you launch LO. 

Preferable to installing the .debs from the LO site is to install the PPA:

[http://handytutorial.com/libreoffice-4-0-x-ppa-is-ready-for-ubuntu-12-04-12-10-13-04/](http://handytutorial.com/libreoffice-4-0-x-ppa-is-ready-for-ubuntu-12-04-12-10-13-04/)

... and:

[https://wiki.ubuntu.com/LibreOffice#Installing_a_newer_version_of_LibreOffice_than_available_via_Ubuntu_repositories](https://wiki.ubuntu.com/LibreOffice#Installing_a_newer_version_of_LibreOffice_than_available_via_Ubuntu_repositories)

And this is where your profile is:

/home/<your_username>/.config/libreoffice/

... where '<your_username>' is just that. Rename the 'user' folder in there to 'user1' or whatever you like. Restart LO. Be warned that any custom setup you've performed to LO will be lost with this procedure. Try it first.

Reinstalling should be/is a last resort.

You might also find this handy:

[https://wiki.documentfoundation.org/UserProfile](https://wiki.documentfoundation.org/UserProfile)

* Just one other thing I've thought of: open LO and Tools>Options>Libreoffice>Print. Is everything okay there? Should be set to 'printer' and not 'print to file'. Now to Libreoffice Writer>Print. The first three under 'Contents' should be ticked but, most importantly, 'left' and 'right' should be ticked under 'Pages'. If they're not, that's your issue. Printing but not told to print any pages.

Just out of curiousity, and you may have mentioned, does it give an error or make like it's printing as per normal, just nothing appears at the printer?

---

### Post by chris-burmajster on 2013-08-03
Thanks, Bucky, for yourcomprehensive reply. 

I downloaded LO (.deb) from LO's website, unistalled LO but found that I didn't know how to install the download, so I reinstalled LO from Software Center. None of this made any difference! The version I have is 4.0.2.2 and the downloaded version is 4.1.0.4. I checked the printer settings in both places that you mention. Everything is ticked just where you say it should be ticked and the printer's name is present and correct. As before, when I try and print, all looks well for about 30 seconds and then the printer icon disappears. Opening the print queue manually, where it claims to have printed successfully and re-starting the last job, it initially says 'printing' and then says 'printer not connected'. It's connected via wi fi and every other program on the computer prints without problem.

I think that I'll try and install via the PPA you mention. If I can't get this to work then I'll have to consider another word processing program.

Thanks again to everybody for your help.

Just tried to install the latest version via your suggestion of the PPA, but somehow it didn't work. I got version 4.0.4.2 instead. Problem remains.:(

---

### Post by Vladlenin5000 on 2013-08-03
```
sudo add-apt-repository ppa:libreoffice/ppa
sudo apt-get update
sudo apt-get dist-upgrade

```

---

### Post by chris-burmajster on 2013-08-03
After having said that everything else prints except LO, I discovered that I could not print a photograph today and the problem was the same - 'printer not connected'. I solved it by deleting the printer, connecting it via USB and re-installing it as a local printer. Now it prints from LO, photos, Firefox, everything. Wi fi connection just doesn't work on Ubuntu.

Thanks to everybody who helped with advice - much appreciated.

---

### Post by EBWQNHD on 2013-08-04
> I solved it by deleting the printer, connecting it via USB and re-installing it as a local printer.

I guess nothing like a full disclosure in the first place;

or us making our assumptions explicit: ie our assumptions were probably that this was a standard USB install

---

### Post by Bucky Ball on 2013-08-05
> **chris-burmajster said:**
> 
Recently I bought a new printer, a Canon Pixma iP7250 which connects 
via wi-fi.

The first post start like this so no, wasn't confusing with USB. ;)

---

### Post by Bucky Ball on 2013-08-05
> **EBWQNHD said:**
> ... our assumptions were probably that this was a standard USB install

The first post starts like this so no, wasn't making that assumption.

[QUOTE=chris-b]Recently I bought a new printer, a Canon Pixma iP7250 which connects
via wi-fi. [/QUOTE]

;)

---

