---
title: "opening PDF files in ubuntu"
date: 2009-09-03
forum: Installation &amp; Upgrades
---

### Post by zaydius1729 on 2009-09-03
so I downloaded ubuntu and i am having trouble opening a PDF file ... it opens on the document reader and th page says :

Please wait...
If this message is not eventually replaced by the proper contents of the document, your PDF
viewer may not be able to display this type of document.
You can upgrade to the latest version of Adobe Reader for Windows®, Mac, or Linux® by
visiting [http://www.adobe.com/products/acrobat/readstep2.html](http://www.adobe.com/products/acrobat/readstep2.html).
For more assistance with Adobe Reader visit [http://www.adobe.com/support/products/](http://www.adobe.com/support/products/)
acrreader.html.
Windows is either a registered trademark or a trademark of Microsoft Corporation in the United States and/or other countries. Mac is a trademark
of Apple Inc., registered in the United States and other countries. Linux is the registered trademark of Linus Torvalds in the U.S. and other
countries


so i would really appretiate any help ... thanks

---

### Post by fatbotgw on 2009-09-03
Have you tried one of the pdf readers from the repositories?  kpdf works well for me.

---

### Post by zaydius1729 on 2009-09-03
i also realized i did not get Evince in my Ubuntu package... is that possible or do i have to do something to see it as part of my applications... please help... i am also having a lot of trouble trying to install acrobat reader... i havea 64 bit ubuntu and got the medibuntu repository since i saw that in one of the forums... an then tried to install acrobat... that didnt work either. please help!!

---

### Post by fatbotgw on 2009-09-03
Are you sure it's installed?

From the command line run:  sudo apt-get install evince

If it says "evince is already the newest version" then it's already installed.  If it doesn't it should go through with the install.

If it's already installed, press Alt+F2 and type evince and then click ok.  That should open it if it's not in the menu.

---

### Post by zaydius1729 on 2009-09-03
thanks that installed evince... but then i tried to open my PDF file and it said i needed the latest version of adobe reader... so i guess i definitely need to have that installed. any way you can help me with that?!!? i would really appretiate it.

---

### Post by fatbotgw on 2009-09-03
When you right click the .pdf what is the default "Open with..." entry?

If you view the properties of a .pdf file and go to the "Open With" tab you can view the programs that you should be able to open the file with.  The selected one is the default choice.

If you want to use evince, click add then click the arrow next to "use custom command" and type evince then click ok.  That will add evince to the list and you will be able to set it as default.

Edit:  If the list shows "Document Viewer" that is evince...

---

### Post by zaydius1729 on 2009-09-03
yea thats the one i am using... and its not working.

---

### Post by fatbotgw on 2009-09-03
According to [this]("http://live.gnome.org/Evince/SupportedDocumentFormats") pdf support is built in.

When you say the Adobe Acrobat install didn't work, what do you mean?  Did it error out or did it just not work?  How were you trying to install it?

---

### Post by zaydius1729 on 2009-09-03
and thats whats confusing me... they are pdf files... and i can open them in acrobat reader if im using vista... but i cant open it on evince.... 

about installing acrobat reader... i went to the medibuntu repository and updated that from the terminal... which worked correctly and then i tried to install acroread using the command that is something along the lines of sudo (something something) acroread.... but it didnt work... this is what it says when i run it:

zayd@zayd-laptop:~$ sudo apt-get install acroread
[sudo] password for zayd: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package acroread is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package acroread has no installation candidate
zayd@zayd-laptop:~$

---

### Post by fatbotgw on 2009-09-03
I'm not sure on that...  Have you tried a "sudo apt-get update" before trying to install?

Have you tried installing it from Synaptic?

Edit:  Have you seen this:  [https://help.ubuntu.com/community/Medibuntu#Note%20about%20Adobe%20Acrobat%20Reader%20(acroread)]("https://help.ubuntu.com/community/Medibuntu#Note%20about%20Adobe%20Acrobat%20Reader%20(acroread)")

---

### Post by -=hazard=- on 2009-10-07
sudo gedit /etc/apt/sources.list

Add the following 2 lines at the end of the file:

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

Save it, then 

sudo apt-get update
sudo apt-get install acroread

---

### Post by hasinasi on 2011-02-24
OK, I know this thread is dead old. Nevertheless, it still comes up in google with a high rank on this topic, so I am replying.  

The problem here is that this is a special kind of pdf file that can only be opened in Adobe Reader (dynamic XFA forms created in Adobe LiveCycle). They also cannot be rendered in other non-Adobe (Windows-, Mac-, etc.) pdf readers.  

I also ran into these documents. On my machine they cannot be read using okular (KDE). They do, however, work in the (free as in beer) Linux version of Adobe Reader. 

See more information here: 
[http://help.quickpdflibrary.com/questions/484/if-this-message-is-not-eventually-replaced-by-the-proper-contents-of-the-document]("http://help.quickpdflibrary.com/questions/484/if-this-message-is-not-eventually-replaced-by-the-proper-contents-of-the-document")  

Hope this helps.

---

