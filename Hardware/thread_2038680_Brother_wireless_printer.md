---
title: "Brother wireless printer"
date: 2012-08-07
forum: Hardware
---

### Post by Miss on 2012-08-07
Brother DCP585CW wireless printer installation

Can anyone help me on how to install a wireless printer into Ubuntu 12.04  please. I have never had to install one before as they have always been hardwired.

Many thanks
Kay

---

### Post by kurt18947 on 2012-08-07
Hi Kay

You could take a look at this thread  post #4
[http://ubuntuforums.org/showthread.php?t=1999216&highlight=brother](http://ubuntuforums.org/showthread.php?t=1999216&highlight=brother)

I uploaded Brother's installer script,  it makes things relatively simple.  To run it you must run the script from an account with SUDO or printer administration privileges.  I've had the best success using HP's JetDirect socket or directly inputting the printer's i.p. address.  I assign a static i.p. address to the printer.  Once I tell the driver to use a certain address I don't want that address to change.  Good luck.

---

### Post by Miss on 2012-08-07
> **kurt18947 said:**
> Hi Kay

You could take a look at this thread  post #4
[http://ubuntuforums.org/showthread.php?t=1999216&highlight=brother](http://ubuntuforums.org/showthread.php?t=1999216&highlight=brother)

I uploaded Brother's installer script,  it makes things relatively simple.  To run it you must run the script from an account with SUDO or printer administration privileges.  I've had the best success using HP's JetDirect socket or directly inputting the printer's i.p. address.  I assign a static i.p. address to the printer.  Once I tell the driver to use a certain address I don't want that address to change.  Good luck.

Ok I've downloaded the file extracted it to my desktop but I don't know what command to use in the terminal to open or use it sorry 

Kind regards
Kay

Ps. I'm new to linux and have no idea what I'm doing.

---

### Post by kurt18947 on 2012-08-07
> **Miss said:**
> Ok I've downloaded the file extracted it to my desktop but I don't know what command to use in the terminal to open or use it sorry 

Kind regards
Kay

Ps. I'm new to linux and have no idea what I'm doing.

No problem, we've all been there.  First off, does the account where the extracted file is have sudo privileges?  Sudo is like Windows administrator,  that account can cause all kinds of problems if used improperly.  I assume you know how to open a terminal.  Do that and type "cd Desktop"  Letter case matters in Linux unlike Windows.  What's the name of the new folder on your desktop?  In a terminal (you can have the terminal open beside the folder so you can copy the name)  type "cd <folder name here> and <enter>  You should see something in the terminal like 
```
everyday@r61:~/Desktop/New_Folder$
```type "dir" <enter>
One of the files should be called 'install.sh'.  If there is, you're almost home.
Type "sudo bash install.sh"
You should be prompted for your password.  Enter it and press 'enter', you'll see no prompts but you should get text scrolling by.  When asked what model you're installing, enter "DCP-585CW".  The script should continue.  You'll be asked if you agree with a couple things, type <y><enter>.  You'll then be asked if you want to specify a connection.  You do.  

I would suggest either "socket" or "i.p."  Before you run the installer I'd suggest assigning a static i.p. address to your printer.  Your printer documentation will tell you how to do that.   I've had mixed results with other network connection types.  I hope this will get you going.   Check back if you have questions.

---

