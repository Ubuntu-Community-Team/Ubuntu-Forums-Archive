---
title: "Trouble setting up a wireless network"
date: 2005-04-27
forum: Hardware &amp; Laptops
---

### Post by young on 2005-04-27
Hi there,

       I am having a trouble setting up a wireless network for ubuntu installed in my 
  laptop.  I am using Acer TravelMate 290, which uses intel centrino (intel   
  pro/wireless 2200BG).  The version of kernel is 2.6.8.1-3-386.  I have recently 
  received a advice from one of the moderators that I should try using ndis 
  wrapper to configure the wireless network.  I did some search on google and 
   happen to find this step by step guide of compilation and installation guide (
   [http://www.linuxelectrons.com/article.php/20040507104718960](http://www.linuxelectrons.com/article.php/20040507104718960).  )
 So far, I have downloaded Windows Driver for the chipset and the 
Linux Driver for the chipset as well.  I don't want to proceed any further 
however, without knowing what do I really need to set up the wireless 
network.  Your suggestions and idea will be highly appreciated, as I am
 really new to the whole procedure.  Thank you in advance.

                                                                                                     Cheers,

                                                                                                                     Young

---

### Post by ernestoongaro on 2005-04-27
Why compile? Ndiswrapper is in the repositories....
```

sudo apt-get install ndiswrapper

```

Now find the drivers for Windows XP and extract them in a temporay folder, you are looking for the .inf and the .sys files - just dump it all really. Ok now you can install the driver.

Open up a terminal, navigate to the folder you put the drivers in and type:
```

sudo ndiswrapper -i NAME_OF_YOUR_INF_FILE.INF
sudo ndiswrapper -m
sudo modprobe ndiswrapper

```

Now, if all went well, your wireless interface will be called wlan0, you can play around with commands like..(some of them have to be run as sudo)
```

iwconfig wlan0     <=shows wireless configuration
iwlist scan wlan0  <=scans for wireless access points
dhclient wlan0     <=attempts to aquire an IP address

```
This should get you a good start.. let me know if you have questions, Good Luck!

---

### Post by young on 2005-04-27
Hi there,

     Thank you for the quick reply, I really appreciate it.  Just had a one question acutally...

[QUOTE=ernestoongaro]Why compile? Ndiswrapper is in the repositories..
Now find the drivers for Windows XP and extract them in a temporay folder, you are looking for the .inf and the .sys files - just dump it all really. Ok now you can install the driver.
[/QUOTE]

    I am presuming that I have to find a driver for my Intel chipset from the Intel website, download it, and burn it into a CD, so that I can use it for the Linux.  Am I right?    


                                                                                                      Young

*PS.  just one more thing actually, I just logged onto my Ubuntu and typed in
 ```
sudo apt-get ndiswrapper
```
and i get the following message:
invalid operation ndiswrapper

   How can I get the files in the repositories when my internet doesn't even work?
 Bit confused actually

---

### Post by jon_hill987 on 2005-04-27
I tryed to follow the instructions you gave (I didn't know ndiswrapper was included either so had been trying to compile it) and got the folowing result:

```
username@pc:~$ sudo apt-get ndiswraper
E: Invalid operation ndiswraper
username@pc:~$ cd /windriver
username@pc:/windriver$
sudo ndiswrapper -i netam722.INF
sudo: ndiswrapper: command not found

```

any ideas?

Scrap that, I worked it out, ndiswrapper wasn't installed. now it tells me that it installed it but it is an invalid driver.

---

### Post by young on 2005-04-27
yeah, that's exactly what I get when I type in 'sudo apt-get ndiswrapper': invalid
  operation ndiswrapper.  The thing is, I am not really sure how to install the  
  ndiswrapper.  I found the source package for the ndiswrapper on this website.
[  http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=99148&release_id=233294](http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=99148&release_id=233294)
 but I am not sure whether or not this is the right ndiswrapper source package or not.  
 If it is, what do I exactly do with this?  (i.e. what is the exact ndiswrapper installation procedure?)

   Anyhow, it is good to find out that someone who had a similar problem with me
 solved that problem:  good for everyone who is using this distro for the first time.
   Thank you very much for your post, I appreciate it.

                                                                                         Cheers,
                                                                                                    Young

---

### Post by jon_hill987 on 2005-04-27
I havn't compleatly solved the problem, It seems that with the dist I was using ndiswrapper wasn't installed, it still give the error that you get when it is. just ignore that step and go to this: ```
sudo ndiswrapper -i NAME_OF_YOUR_INF_FILE.INF
sudo ndiswrapper -m
sudo modprobe ndiswrapper
```, it may be your driver will work. mine dosn't seem to.

---

### Post by jon_hill987 on 2005-04-27
Ok here is the latest from my laptop....

```
root@JON:/windriver# ndiswrapper -i netam772.inf
Installing netam772
cp: cannot stat `netam772.inf': No such file or directory
root@JON:/windriver# ndiswrapper -l
Installed ndis drivers:
netam772        invalid driver!
root@JON:/windriver# ndiswrapper -m
modprobe config already contains alias directive

root@JON:/windriver# modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted

```

I don't know why my drive is invalid

The wifi card uses the AMD Am1772 chipset

---

### Post by az on 2005-04-27
HEY!

Please not that

apt-get ndiswrapper 

is incorrect.   It should be

sudo apt-get install ndiswrapper



You do not need to be on the internet - it is on your cd.

EDIT:  This problem can be avoided by just using synaptic.  Use synaptic instead of the command line for installing packages.

---

### Post by young on 2005-04-27
Hi everyone,


            I have managed to solve the wireless issue.  It is working on my ubuntu.  I 
      wouldn't imagine myself to be on this stage without everyone's help.  Thank you 
     so much!!  What I did was to check the current setting of my router by typing in
    iwlist eth1 scanning ( before you do this, type in iwconfig to figure out where 
    exactly  the driver for wireless chipset is installed....it might not be eth1 like mine).

     What I got when I typed in 'iwlist eth1 scanning' is the following:

     ```
 Scan completed:
                Cell 01 - Address:  00:04:E2:A2:21:14
                              ESSID: "SMC"
                              Protocol: ieee 802.11g
                              Mode: Master
                              Channel: 6
                              Bit Rate:54Mb/s
                              Extra: Rates(Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                              Extra: RSSI: -52 dBm
                              Encryption key: on 
```

   So what I did was to disable the encryption key.  Depending on the model
of the wireless router, you might have to read the manual and follow through the 
instruction.

   Now this is only one way of solving the problem,  but I am sure there might be more clever ways of solving the issue.  If there are, please feel free to let me know.
   Anyhow, once again, thank you for all your help.

                                                                                                  cheers,

                                                                                                              Young

---

### Post by ernestoongaro on 2005-04-28
Sorry Young, glad you figured it out, I forgot the install in apt-get install, DOH! ](*,)

---

