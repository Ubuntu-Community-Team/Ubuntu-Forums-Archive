---
title: "How to install wine?"
date: 2005-12-27
forum: Installation &amp; Upgrades
---

### Post by torzan on 2005-12-27
Hi,
Im quite new to linux/Ubuntu.
I have tried to follow the instructions  (wine hq) on installing WINE on a pc running UBUNTU 5.10.
But when I open Synaptic package manager I dont get the choices described in "http://www.winehq.com/site/download-de"
I can not find choices  "Settings->Repositories" and i dont find "add" function.

Do i start the wrong Synaptic? I choose System->Administration->Synaptic Package administrator.

Torzan

---

### Post by ronb on 2005-12-27
Torzan,

You are starting Synaptic correctly.  On the tool bar is a Search button.  Click on that and enter wine in the text box.

I'm new to linux/Ubuntu, also, but I think this will bring up a list of packages that you're looking for.  You can choose from the list what you want to install.  

Hope that works.

Ron

---

### Post by 504harry on 2005-12-27
FWIW I understand that Synaptic only searches for packages already present (confusing huh?). You have to supply a "List*" to make the search wider and to go outside the Ubuntu "officiial software" you need Repository Lists - these then open up vast amounts of software - but it's not supported by Ububtu and so there is a degree of trying to protect us from ourselves. 
/
In Windows there never seemed to be a scheme to use the Mag cover-disc software demos without getting at the Registry - hence Uninstalling some "free trial" software was a Trial in itself.
- I suspect Ubuntu isn't any better. in this regard.....and I have been confused by the need to reload/upgrade my installation the moment it has been installed. I guess it is all part of the Learning process  but one that Newbies all seem to take at their peril. If you "don't know" then everything is fraught with danger.
/
This is part of the reason why Win need not fear being displaced by Linux - there is not one voice that sets goals for it to be easier to get it working. 
FWIW I suggest ONE HOUR and during that time you should be able to:
Send/receive emails using an existing ISP
Download .pdf document to your printer (=Java instructions, see next item)
Install Java into Firefox browser.
Download (a camera) file via USB and alter the colours/cropping/contrast before saving it and printing.
Create a Memo. \\colour and format it, using two styles/sizes of typeface sending it as an email (to a friend), print it and save it in pure ASCII and as a .PDF file.
Since these tasks take  ten minutes, the **Installation **should be no longer than **50 mins **- some reduction in the size of _OpenOffice_ *Gnome* and _GIMP_ might be performed to advantage - software has a habit of growing over time; out of proportion to the ease-of-use, or user-benefits.   "More " is rarely "better"
* ( More correctly  it's a **Sources.List **)I was given one of these "Lists"by someone that understood Ubuntu/Sympatic but sadly I never dared use it. He was very ,much a "Command-line" chappie and I hit upon  a graphical Sympatic by chance. AS Ububtu advances, some of the "old dodges" become unnecessary IMHO...... It is very confusing and I look forward to a definitive answer.

---

### Post by kaamos on 2005-12-27
(Hardly understood a word of the post above)

Anyway, installing wine can be done like this. Open a terminal and type these commands
```

sudo su
echo "deb http://wine.sourceforge.net/apt/ binary/" >> /etc/apt/sources.list
apt-get update
apt-get install wine
exit

```
You can now start a windows program with wine like this
```
wine program.exe
```

---

### Post by kaamos on 2005-12-27
[QUOTE=504harry]* ( More correctly  it's a **Sources.List **)I was given one of these "Lists"by someone that understood Ubuntu/Sympatic but sadly I never dared use it. He was very ,much a "Command-line" chappie and I hit upon  a graphical Sympatic by chance.[/QUOTE]

Reading these could clarify some things:
[https://wiki.ubuntu.com/Repositories](https://wiki.ubuntu.com/Repositories)
[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

---

### Post by 504harry on 2005-12-27
kaamos you know you stuff - in effect aren't you are avoiding the use of Synaptic? - - so the original thread, on using Synaptic was false - although I didn't know it, my suggestion retained Synaptic .......your solution looks a lot simpler, but would not be attempted/available to a novice. ...but it looks a great fix
/
Does this mean that after installing Wine it is "outside" synaptic's capabilities? 
I wanted to try Inkscape and ended up using their web-site download-option.......in effect I was not using Synaptic......is this similar?..... 
/
Does synaptic add these new progs (eg for updating later) or will they be forever Outside - 
I found the 5.04 upgrades easy enough, although a little unsure what had been happening and at one stage managed to mess up OpenOffice - but don't understand why/how. On Broadband these update take so little time and the file-names have little meaning (etc)


Thanks.

---

### Post by 504harry on 2005-12-27
[QUOTE=kaamos]Reading these could clarify some things:
[https://wiki.ubuntu.com/Repositories](https://wiki.ubuntu.com/Repositories)
[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)[/QUOTE]
Thanks, I have looked and learned.....will do it again before attempting any updates, thanks....knowing where to look is a great help.
H.

---

### Post by kaamos on 2005-12-27
[QUOTE=504harry]kaamos you know you stuff - in effect aren't you are avoiding the use of Synaptic? - - so the original thread, on using Synaptic was false - although I didn't know it, my suggestion retained Synaptic .......your solution looks a lot simpler, but would not be attempted/available to a novice. ...but it looks a great fix[/quote]
I was not using synaptic here because it's harder to explain well what should be done because it's a graphical application. In this case it was easier to just say "copy & paste these commands". This, of course, is not a good thing for understanding how installing software works. However the instructions in winehq seem to be quite good, and the only way I think I could have been able to help with synaptic would have been to post screenshots with red circles and text "click here and then here".

So this was a quick, but not the best solution. 

[QUOTE=504harry]Does this mean that after installing Wine it is "outside" synaptic's capabilities? 
I wanted to try Inkscape and ended up using their web-site download-option.......in effect I was not using Synaptic......is this similar?..... [/quote]
No, synaptic is a graphical front end to a program called apt. So everything that can be done on the command line with apt, can be done with synaptic. And using synaptic is often much easier..

If you downloaded a .deb file from inkscapes web page, then this was about the same as using synaptic. However if the file was something else it was not. Anyway, it would have been easier just to open synaptic and install inkscape from there.
[QUOTE=504harry]Does synaptic add these new progs (eg for updating later) or will they be forever Outside - 
I found the 5.04 upgrades easy enough, although a little unsure what had been happening and at one stage managed to mess up OpenOffice - but don't understand why/how. [/QUOTE]
The update-manager that updates the programs also uses apt, so all the packages installed with synaptic can be updated with it when never versions are added to ubuntu repositories.

Hope this helps a little to undestand how synaptic works. :)

---

### Post by jensbrown on 2006-01-03
Ok - Wine is live on my machine, now what :)

I have a Windows partition already.  Do I in some fashion direct wine to open Specific applications from the Program Files directory in Windows XP, or load the application in Unbuntu using Wine.

....are there any resources available....?

---

### Post by dcstar on 2006-01-03
[QUOTE=jensbrown]Ok - Wine is live on my machine, now what :)

I have a Windows partition already.  Do I in some fashion direct wine to open Specific applications from the Program Files directory in Windows XP, or load the application in Unbuntu using Wine.

....are there any resources available....?[/QUOTE]
First open a user terminal and do "winecfg" to set up your system (especially the Drives!).

Installing "winetools" is also handy for installing and configuring your setup.

To run windows programs, open a user terminal and type "wine progamnamewhateveritis.exe", or use Nautilus and run the .exe files as you would in Windows.

---

