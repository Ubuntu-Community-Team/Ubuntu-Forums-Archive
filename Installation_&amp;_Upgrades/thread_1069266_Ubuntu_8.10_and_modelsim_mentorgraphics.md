---
title: "Ubuntu 8.10 and modelsim mentorgraphics"
date: 2009-02-13
forum: Installation &amp; Upgrades
---

### Post by edgarcgarzon on 2009-02-13
I have a problem installing Modelsim on Ubuntu 8.10 I really don't know what is wrong but I put all the files on a single folder and download all the files corresponding to my OS. but still appear a error message when try to run the file install.linux.

---

### Post by Partyboi2 on 2009-02-14
Are you able to post the error message you are getting?

---

### Post by |mynick| on 2009-02-14
Maybe this could help:

```
sudo chmod -744 install.linux
./install.linux
```

You have to make executable the install.linux file. when you download it, it's not. 

Bye

---

### Post by edgarcgarzon on 2009-02-14
thanks that works perfectly...I'm newie with linux then a simple commands like those ones are new for me. anyway thanks.

---

### Post by edgarcgarzon on 2009-02-15
I have a new problem with license because when I try to run ./vsim from 
mydirectory/modeltech/linux I have an error message that referes to the license. 

I alredy try to
export LM_LINCESE_FILE=mydirectory/modeltech/linux/license.dat

but doesn't still works. Even  I tried this, I really not sure because I can't find the license.dat anywhere. And when I download the modelsim from the mentorgraphics website it didn't arrive to my mail, like when I used it with Windows.

thanks to help this newie.

---

### Post by dimamali on 2009-03-09
I am having the exact same problem. I have installed the linux edition and i get the same error message everytime i try to vcom.
Any solutions yet?

---

### Post by karlr42 on 2009-03-09
Did you pay for a license? I assume this is the Linux version of Modelsim SE? I use Modelsim PE Windows version using Wine, and it links up with the Linux version of Xilinx just fine.

---

### Post by shafqat on 2009-03-15
please somebody help me, i  downloaded the modelsim for Linux from modelsim website, and want to install it, but when i try ./install-Linux
it gave me error permission denied... i tried the above method
 
sudo chmod -744 install.linux
./install.linux

but it also does not work... i have to do my lab please help me quickly:(:(

---

### Post by tbranham on 2009-10-08
> **karlr42 said:**
> Did you pay for a license? I assume this is the Linux version of Modelsim SE? I use Modelsim PE Windows version using Wine, and it links up with the Linux version of Xilinx just fine.

Hey, I know this tread is kind-of old, but karlr42, can you tell me *how* you get Modelsim PE (through wine) and Xininx (native linux) to talk to one another? I've been scratching my head over that for a couple of hours now, and I just can't seem to make them work together... both seem to be installed and working properly on their own.

---

### Post by tommpogg on 2011-07-01
> **tbranham said:**
> Hey, I know this tread is kind-of old, but karlr42, can you tell me *how* you get Modelsim PE (through wine) and Xininx (native linux) to talk to one another? I've been scratching my head over that for a couple of hours now, and I just can't seem to make them work together... both seem to be installed and working properly on their own.

1) open xilinx ise.

2) under eit/preferences, select Integrated Tools.

3) Edit the field "Model Tech Simulator" in order to make it point to you Modelsim executable (vsim). To do this enter the path of vsim: it should be located somewere in the (hidden) folder
[INDENT]/home/*username*/.wine/[I]modelsim_installation path
[/I][/INDENT]where *username* is the name of your home directory; *modelsim_installation_path* is where you have installed Modelsim (with WINE).
Notice that vsim could be in a subfolder. Just look for it

If it doesn't work, take a look [here]("http://groups.google.com/group/modelsim-pe-student-edition/browse_thread/thread/e3ad0558423d3419")

---

### Post by cariboo on 2011-07-01
8.10 isn't supported any more. Things have changed enough since, that your solution may no work. 2 year old thread closed.

---

