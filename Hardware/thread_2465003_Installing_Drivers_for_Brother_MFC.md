---
title: "Installing Drivers for Brother MFC"
date: 2021-07-18
forum: Hardware
---

### Post by daniell59 on 2021-07-18
I would greatly appreciate it if somebody could walk me through the steps so that I can use the following with Ubuntu 20.04 64

Brother MFC-7340
I need help from step 4 onward. Any assistance will be appreciated.

[https://support.brother.com/g/b/downloadhowto.aspx?c=us&lang=en&prod=mfc7340_us_as&os=128&dlid=dlf006893_000&flang=4&type3=625](https://support.brother.com/g/b/downloadhowto.aspx?c=us&lang=en&prod=mfc7340_us_as&os=128&dlid=dlf006893_000&flang=4&type3=625)

---

### Post by him610 on 2021-07-18
Ok, lets see if we can help to get your MFC-7340 installed. It looks like you have completed step 4. Is that correct?
I assume you downloaded the correct ***Driver Install Tool*** for your device. You probably should have your printer powered on and connected.

For step 5, you need to have a terminal open in the directory/folder where you performed the step 4 'gunzip' operation.
Enter your password when it asks for it. After you enter it, you become ***root*** You will need *root* privileges to complete the next few steps.
> Step5. Get superuser authorization with the "su" command or "sudo su" command. Run this from command line...
```
sudo su
```
You should have a hash or crunch (#) for your prompt now which indicates you have* root* privileges.
> Step6. Run the tool:

Command: bash linux-brprinter-installer-*.*.*-* Brother machine name
e.g. bash linux-brprinter-installer-2.2.2-2 MFC-7340 Run this from command line...
```
bash linux-brprinter-installer-2.2.2-2 MFC-7340

```
Just follow the prompts; it will take a few minutes to run.
> Step7. The driver installation will start. Follow the installation screen directions.
 

 When you see the message "Will you specify the DeviceURI ?",

 For USB Users: Choose N(No)  **[COLOR="#FF0000"]<-- This is for you[/COLOR]**
 For Network Users: Choose Y(Yes) and DeviceURI number.

The install process may take some time. Please wait until it is complete.
Your MFC-7340 should be installed now.
If you still have root privileges, you need to terminate root privileges by ```
exit
```
You should probably print a test page just to be sure it works.
I have successfully completed network installation for a Brother MFC-7360N many times, but never for a one connected with USB cable,

---

### Post by daniell59 on 2021-07-19
> **daniell59 said:**
> I would greatly appreciate it if somebody could walk me through the steps so that I can use the following with Ubuntu 20.04 64

Brother MFC-7340
I need help from step 4 onward. Any assistance will be appreciated.

[https://support.brother.com/g/b/downloadhowto.aspx?c=us&lang=en&prod=mfc7340_us_as&os=128&dlid=dlf006893_000&flang=4&type3=625](https://support.brother.com/g/b/downloadhowto.aspx?c=us&lang=en&prod=mfc7340_us_as&os=128&dlid=dlf006893_000&flang=4&type3=625)

I am ashamed to say it, but I could not even get to step 4. I must be doing something wrong in the terminal. It kept saying no such file.

---

### Post by daniell59 on 2021-07-19
Sorry to say. I am still confused. I was able to do step 5 but not step 4.

daniel@daniel-P5Q-PRO:~$ cd Downloads
daniel@daniel-P5Q-PRO:~/Downloads$ gunzip linux-brprinter-installer-2.1.1-1.gz
gzip: linux-brprinter-installer-2.1.1-1.gz: No such file or directory
daniel@daniel-P5Q-PRO:~/Downloads$

---

### Post by coffeecat on 2021-07-19
The terminal is telling you that there is no linux-brprinter-installer-2.1.1-1.gz file in the Downloads folder. I note that linux-brprinter-installer-2.1.1-1.gz is the "for example" version given in your linked instructions. More than likely you have a later version, not 2.1.1-1.

Let's see which version you have. Make sure you are still in the Downloads folder in the terminal, and run:

```
ls linux-br*
```

And post the output.

---

### Post by daniell59 on 2021-07-19
daniel@daniel-P5Q-PRO:~/Downloads$ ls linux-br*
linux-brprinter-installer-2.2.2-2
daniel@daniel-P5Q-PRO:~/Downloads$

---

### Post by coffeecat on 2021-07-19
Then your gunzip command needs to be:

```
gunzip linux-brprinter-installer-2.2.2-2.gz
```

I'm assuming you meant linux-brprinter-installer-2.2.2-2.gz and not linux-brprinter-installer-2.2.2-2 as you posted. Was that a typo omission? Your link offers to download a *.gz file. 

When you get to step 6, you'll need to modify the command given to the version number you have. It'll most certainly be 2.2.2-2 again, but check with *ls* or with an open file browser that the installer you have is linux-brprinter-installer-2.2.2-2 first. Also, don't type in MFC-J880DW as the machine name. That's just a "for example" again in the instructions. Your model number is different. When following instructions like those, don't just copy and paste. You need to check details like that and modify as appropriate. "e.g." (exempli gratia) means "for example".

---

### Post by daniell59 on 2021-07-19
> **coffeecat said:**
> Then your gunzip command needs to be:

```
gunzip linux-brprinter-installer-2.2.2-2.gz
```

I'm assuming you meant linux-brprinter-installer-2.2.2-2.gz and not linux-brprinter-installer-2.2.2-2 as you posted. Was that a typo omission? Your link offers to download a *.gz file. 

When you get to step 6, you'll need to modify the command given to the version number you have. It'll most certainly be 2.2.2-2 again, but check with *ls* or with an open file browser that the installer you have is linux-brprinter-installer-2.2.2-2 first. Also, don't type in MFC-J880DW as the machine name. That's just a "for example" again in the instructions. Your model number is different. When following instructions like those, don't just copy and paste. You need to check details like that and modify as appropriate. "e.g." (exempli gratia) means "for example".

I appreciate your help. This may be too much for me. I am still stuck on step 4. I will take a break from this. Maybe later in the day it will become clearer to me. Thanks again for your kind and informative replies.

---

### Post by coffeecat on 2021-07-19
> **daniell59 said:**
> I appreciate your help. This may be too much for me. I am still stuck on step 4. I will take a break from this. Maybe later in the day it will become clearer to me. Thanks again for your kind and informative replies.

You're welcome. I've just noticed something else. The zip file that you can download from your link has the filename linux-brprinter-installer-2.2.2-2.gz. When you unzip it, you get a single file in the same directory with the filename linux-brprinter-installer-2.2.2-2. That was the same filename that you posted in post #6 as the message from bash after you ran the "ls linux-br*" command. Since that was all ls listed, I don't think you have already unzipped the *.gz, which is why I assumed you had simply omitted the ".gz" when posting. Worth checking that. You can inspect the contents of the Downloads folder with the file manager if you prefer.

And then step 6 will probably be:

```
bash linux-brprinter-installer-2.2.2-2 MFC-7340
```

Based on the model number you gave in post #1.

Enjoy your break and then see if you can follow the logic behind the various filenames. If you can see what is going on, it'll pay dividends for the future rather than following instructions blindly.

linux-brprinter-installer-2.2.2-2.gz is a gzip archive. linux-brprinter-installer-2.2.2-2 is the actual installer wrapped inside the archive. It is simply a text file that runs as a script. 2.2.2-2 in both filenames is the version number. That's worth understanding as you'll probably come across similar in the future where the numbers in the filename change according to the version number.

Good luck!

---

### Post by daniell59 on 2021-07-20
Thanks to all. I now have printer function. I guess there is still life left in this 75 year old brain.
I will later see about scanning.

---

### Post by daniell59 on 2021-07-20
I would appreciate help in getting the scanner to work. The scanner is detected.

---

### Post by daniell59 on 2021-07-20
The scanner is now working. Thanks to all that gave me the confidence to persevere.

---

### Post by him610 on 2021-07-20
How about the fax capability? Do you have that working? Unless you don't have a landline.

---

### Post by daniell59 on 2021-07-21
> **him610 said:**
> How about the fax capability? Do you have that working? Unless you don't have a landline.

Years ago I used the machine only to send and receive faxes. As of late, I don't have much use for the fax capacity. I had had a compact HP laser printer on my desk with a dedicated scanner. The printer is no longer functioning. This machine is a temporary replacement until I buy another laser printer. Also, I could never get the Epson scanner to work with Ubuntu 20.04. A forum member even gave me instructions on the phone. He also gave up. To use it, I have to go to Windows.

---

### Post by daniell59 on 2021-07-25
I'm Back!
I just noticed PC fax that was automatically installed in windows. I would like to install it in Linux. If I can do so, I will get rid of windows. Since I have the printer and scanner working, I don't want to chance ruining what I have because of a paucity of knowledge. Assistance will be appreciated.
[https://support.brother.com/g/b/faqend.aspx?c=us&lang=en&prod=mfcl3750cdw_us_eu_as&faqid=faq00100716_000](https://support.brother.com/g/b/faqend.aspx?c=us&lang=en&prod=mfcl3750cdw_us_eu_as&faqid=faq00100716_000)

---

### Post by linuux on 2021-07-25
> **daniell59 said:**
> I'm Back!
I just noticed PC fax that was automatically installed in windows. I would like to install it in Linux. If I can do so, I will get rid of windows. Since I have the printer and scanner working, I don't want to chance ruining what I have because of a paucity of knowledge. Assistance will be appreciated.
[https://support.brother.com/g/b/faqend.aspx?c=us&lang=en&prod=mfcl3750cdw_us_eu_as&faqid=faq00100716_000](https://support.brother.com/g/b/faqend.aspx?c=us&lang=en&prod=mfcl3750cdw_us_eu_as&faqid=faq00100716_000)

If it works, you could always install Windows in a Virtual Machine in your Ubuntu partition.   E.g. Virtual Box, then install Windows as a client and install your printer software there just in case, the Linux version stops working for some reason.

---

### Post by daniell59 on 2021-07-25
> **linuux said:**
> If it works, you could always install Windows in a Virtual Machine in your Ubuntu partition.   E.g. Virtual Box, then install Windows as a client and install your printer software there just in case, the Linux version stops working for some reason.

I did not install the Linux version. I would have a problem with virtual machine. My computer is old and has limited resources. 4 GIG of RAM. I am waiting for the Ryzen 5000G series to hit the retail market. I may then build a new machine.

---

### Post by linuux on 2021-07-25
> **daniell59 said:**
> I did not install the Linux version. I would have a problem with virtual machine. My computer is old and has limited resources. 4 GIG of RAM. I am waiting for the Ryzen 5000G series to hit the retail market. I may then build a new machine.Oh right.... yes, can be a problem.

I am hoping to get a Ryzen system, too...although, I will see what Intel is also offering at the time I can shop around.  

I don't think you need to dedicate much RAM to Windows, however, if you only use it for printing but 4GB is pretty low for that.  I only have 8gb total.  I was thinking of upgrading it to 16gb eventually but my current machine is getting pretty old.  We'll see...

---

