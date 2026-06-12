---
title: "Brother MFC-J280W printer"
date: 2014-08-27
forum: Hardware
---

### Post by user_linux on 2014-08-27
Hello,
I am trying to install the printer into ubuntu 12.04 LTS. But when I input model name in the printer, it gives me message can't find  driver. I have tried typing "mfc-j280w", "MFC-J80w" as appearing on printer top and so on by alternating upper and lower case but of no avail. Pls help!

---

### Post by kurt18947 on 2014-08-28
I doubt that printer is supported "out of the box".  I've had quite good luck using Brother's installer script.  It is run from a terminal. It's found here:

[http://support.brother.com/g/s/id/linux/en/faq_prn.html?c=us_ot&lang=en&redirect=on#f00104](http://support.brother.com/g/s/id/linux/en/faq_prn.html?c=us_ot&lang=en&redirect=on#f00104)

Brother has a newer version that also installs the scanner driver although scanner install requires some other tweaks. I have a copy but I'm not certain where i found it.

Here is Brother's linux driver page including instructions.  Be aware that some of the information in those pages is pretty dated or may not apply to Ubuntu.

[http://support.brother.com/g/s/id/linux/en/index.html?c=us_ot&lang=en&comple=on&redirect=on](http://support.brother.com/g/s/id/linux/en/index.html?c=us_ot&lang=en&comple=on&redirect=on)

Let us know how you get on.

Edit: I found a simpler means to download the latest Brother driver installer for linux:

[http://support.brother.com/g/b/downloadend.aspx?c=gb&lang=en&prod=dcp115c_eu_as&os=127&dlid=dlf006893_000&flang=4&type3=625](http://support.brother.com/g/b/downloadend.aspx?c=gb&lang=en&prod=dcp115c_eu_as&os=127&dlid=dlf006893_000&flang=4&type3=625)

Be sure you're in an account with sudo privileges.  Open a terminal and change to the folder where the extracted script is.  Type "sudo bash linux-brprinter-installer-2.0.0.1".  You'll be prompted for your sudo password.  The script will start and prompt you for your printer model.  Remeber in linux letter case counts so type "MFC-J280W" and answer the prompts as they display.

---

### Post by pdc on 2014-08-28
kurt has given you a really good pointer there to the Brother installer script; he is an expert on these things; you might find the phrase "Open a terminal and change to the folder where the extracted script is" a wee bit tricky; (after using linux for a while it will roll off your tongue!!)

if you click to download the [COLOR="#EE82EE"]Brother Installer Tool[/COLOR] and select **SAVE** as it starts to download, it should end up in your [COLOR="#0000FF"]Downloads[/COLOR] directory

so my take on the commands needed would be; after you open a terminal..............(find it with your Dash search space) ........

if you copy these commands; and paste them into the terminal; line by line; and hit the ENTER key after each paste .............................

> [COLOR="#FF0000"]cd Downloads[/COLOR]

> [COLOR="#FF0000"]gunzip linux-brprinter-installer-2.0.0-1.gz[/COLOR]

> [COLOR="#FF0000"]sudo bash linux-brprinter-installer-2.0.0-1 MFC-J280W[/COLOR]

and it should install there

---

### Post by kurt18947 on 2014-08-30
> **pdc said:**
> kurt has given you a really good pointer there to the Brother installer script; he is an expert on these things; you might find the phrase "Open a terminal and change to the folder where the extracted script is" a wee bit tricky; (after using linux for a while it will roll off your tongue!!)

if you click to download the [COLOR=#EE82EE]Brother Installer Tool[/COLOR] and select **SAVE** as it starts to download, it should end up in your [COLOR=#0000FF]Downloads[/COLOR] directory

so my take on the commands needed would be; after you open a terminal..............(find it with your Dash search space) ........

if you copy these commands; and paste them into the terminal; line by line; and hit the ENTER key after each paste .............................







and it should install there

Thanks PDC. There's probably a GUI way to extract the Brother download.  Simply right-click on the downloaded file in nautilus and 'extract' should be one of the options. Choose the folder where you want to file extracted.  A couple things regarding terminal use.  One is that letter case matters.  When I was greener than I am now, I was typing "cd desktop" and I'd get a reply that no folder by that name could be found.  I KNEW there was a desktop folder!!!!.  Fuss, Fume, oh wait............ cd **D**esktop and there it was :oops:.  A second tip is when faced with long file names in the terminal, type the first 3 or 4 letters then press the 'tab' key.  There's a good chance it will fill in the file name and greatly reduce the likelihood of typos. If that doesn't work for some reason, copy paste works too.  Type 'dir' and get the list of files in the folder containing the desired folder.  Highlight the desired file, click 'edit'-'copy' in the terminal's menu.  Put the insert point in the command line where you want it and  click 'edit' - 'paste'.  Again to eliminate typos.

---

### Post by user_linux on 2014-08-30
Thank you very much for you reply. I have done what you mentioned, but my terminal screen is keep going for half an hour now, it doesn't stop, installing printer doesn't take that long. It keeps installing new packages and asks me to put y or n for new packages.
thanks.
> **pdc said:**
> kurt has given you a really good pointer there to the Brother installer script; he is an expert on these things; you might find the phrase "Open a terminal and change to the folder where the extracted script is" a wee bit tricky; (after using linux for a while it will roll off your tongue!!)

if you click to download the [COLOR=#EE82EE]Brother Installer Tool[/COLOR] and select **SAVE** as it starts to download, it should end up in your [COLOR=#0000FF]Downloads[/COLOR] directory

so my take on the commands needed would be; after you open a terminal..............(find it with your Dash search space) ........

if you copy these commands; and paste them into the terminal; line by line; and hit the ENTER key after each paste .............................







and it should install there

---

### Post by user_linux on 2014-08-30
Thanks very much for the help, worked like a charm, do you guys know how to install scanner as well?

---

### Post by pdc on 2014-08-30
> [COLOR="#EE82EE"]do you guys know how to install scanner as well? [/COLOR]

as I understand it, the Brother Installer Too should install the needed scanner drivers as well 

with your proficiency at the terminal, copy this command and paste it into your terminal > [COLOR="#FF0000"]dpkg -l | grep brscan[/COLOR] .........it is asking your debian package manager to list what it has in its records on brscan, the brother scanner 

____________________________

you can also check that the Brother is mentioned in the file 60-libsane.rules with the command 

> [COLOR="#FF0000"]gedit /etc/udev/rules.d/60-libsane.rules[/COLOR]

..............the file opens as READ-ONLY so you can't change it .......................

scroll to the end (or use control F as finder) and look for the entry

> [COLOR="#EE82EE"]# Brother 
 ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"[/COLOR] 

.................if you see that, the installer has been at work .................

(part of the install for a brother scanner is creating this entry)

---

### Post by kurt18947 on 2014-08-31
> **pdc said:**
> as I understand it, the Brother Installer Too should install the needed scanner drivers as well 

with your proficiency at the terminal, copy this command and paste it into your terminal  .........it is asking your debian package manager to list what it has in its records on brscan, the brother scanner 

____________________________

you can also check that the Brother is mentioned in the file 60-libsane.rules with the command 



..............the file opens as READ-ONLY so you can't change it .......................

scroll to the end (or use control F as finder) and look for the entry



.................if you see that, the installer has been at work .................

(part of the install for a brother scanner is creating this entry)

Really?  That's a welcome improvement.  There's one other potential problem documented here:

[http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#f00101](http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#f00101)

Same advice from PDC applies.  Open /user/lib and usr/lib/sane and make sure the listed files are present for your scanner.  Copy them as instructed if they aren't in the proper place.  To use the scanner over a network it's pretty simple, one line in a terminal.

```

brsaneconfig(2,3,4)  -a  name=(name  your  device)  model=(model  name)  ip=xx.xx.xx.xx

```

---

