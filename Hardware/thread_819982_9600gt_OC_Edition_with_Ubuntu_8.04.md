---
title: "9600gt OC Edition with Ubuntu 8.04"
date: 2008-06-05
forum: Hardware
---

### Post by AMD_infinium05 on 2008-06-05
hi! guys,

im really having trouble installing my Inno3D 9600gt OC Edition vcard on ubuntu.

I have downloaded the latest driver from nvidia ( [http://www.nvidia.com/object/linux_display_amd64_173.14.05.html](http://www.nvidia.com/object/linux_display_amd64_173.14.05.html) ) and when i try to type in the following command:

"sh NVIDIA-Linux-x86_64-173.08-pkg2.run"

it says " cannot open file / cannot read the file " or something like that...

I am NEW TO UBUNTU and linux. :KS

Informations, explanations why im getting that error and steps on how to setup this are much appreciated.. thnx!

my complete system specs:
AMD Athlon64 X2 5200+ 2.6ghz @ 3.1ghz
Emaxx NF7050HD-Pro
2GB Corsair XMS2 1gb * 2 DDR800 @ DDR890 dual channel
160GB Seagate Barracuda SATA
Inno3D 9600GT 512mb 256bits OC Edition
Silverstone ST50F 500w PSU
Creative Sounblaster Audigy 2 5.1
BTC DVD-RW/DL 16x

SOLVEd by:::: [http://ubuntuforums.org/showpost.php...71&postcount=6](http://ubuntuforums.org/showpost.php...71&postcount=6)   < thanks to this man! you're the man

---

### Post by hotweiss on 2008-06-06
> **AMD_infinium05 said:**
> hi! guys,

im really having trouble installing my Inno3D 9600gt OC Edition vcard on ubuntu.

I have downloaded the latest driver from nvidia ( [http://www.nvidia.com/object/linux_display_amd64_173.14.05.html](http://www.nvidia.com/object/linux_display_amd64_173.14.05.html) ) and when i try to type in the following command:

"sh NVIDIA-Linux-x86_64-173.08-pkg2.run"

it says " cannot open file / cannot read the file " or something like that...

I am NEW TO UBUNTU and linux. :KS

Informations, explanations why im getting that error and steps on how to setup this are much appreciated.. thnx!

my complete system specs:
AMD Athlon64 X2 5200+ 2.6ghz @ 3.1ghz
Emaxx NF7050HD-Pro
2GB Corsair XMS2 1gb * 2 DDR800 @ DDR890 dual channel
160GB Seagate Barracuda SATA
Inno3D 9600GT 512mb 256bits OC Edition
Silverstone ST50F 500w PSU
Creative Sounblaster Audigy 2 5.1
BTC DVD-RW/DL 16x

Try this:
1. sudo apt-get install build-essential
2. sudo apt-get remove nvidia*
3. Ctrl-Alt-F1
4. sudo /etc/init.d/gdm stop
5. sudo su
6. sh ./NVIDIA-Linux-x86-173.14.05-pkg1.run
7. go through all the prompts
8. restart

---

### Post by AMD_infinium05 on 2008-06-06
after step 3,4,5

at step 6

cant open the file

---

### Post by reidbold on 2008-06-06
6a. sudo chmod +x NVIDIA....
6b. old #6

The problem is the file doesn't have execution rights, 6a fixes that.

---

### Post by AMD_infinium05 on 2008-06-06
6a doesnt work, it seems not to find the file...

the file is located on desktop.... what should be the right path?
with the command? i renamed the driver file to Nvidia so now it is nvidia.run

sudo chmod +x ...  ?

---

### Post by thideras on 2008-06-06
> **AMD_infinium05 said:**
> 6a doesnt work, it seems not to find the file...

the file is located on desktop.... what should be the right path?
with the command? i renamed the driver file to Nvidia so now it is nvidia.run

sudo chmod +x ...  ?It does not matter where the file is, you just need to browse to it.  If it is on your desktop, you want to type:

```
cd /home/[username]/Desktop
```


That will bring you to the desktop so you can run the file or change permissions.

---

### Post by reidbold on 2008-06-07
Sorry, guess that was too brief:confused:  
Here is the long version:


[LIST]
[*]open the console
[*]cd Desktop
[*]sudo chmod +x NVIDIA<tab> (tab is filename completion, because typing out the entire driver line would be hard... tab is easy)
[*]sudo ./NVIDIA<tab>
[/LIST]
That should get the installer running.

---

### Post by AMD_infinium05 on 2008-06-08
i'll try that... thanx!!! i'll be back in a while here for feedback

---

