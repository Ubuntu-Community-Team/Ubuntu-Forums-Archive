---
title: "HP Pavillion g6 is overheating since Ubuntu 12.04 installation."
date: 2012-08-08
forum: Hardware
---

### Post by ruslan kim on 2012-08-08
Hey everyone!
I have successfully installed Ubuntu 12.04 (64 bit) yesterday and came across a small problem. My laptop is overheating badly, it becomes very hot in 5 or 10 minutes after I start it. The fan is going crazy, but it doesn't help to cool the PC. It is very strange, because it didn't act this way when I was on Windows 7.

What can it be? I have a HP Pavillion g6.
P.S. Please explain it simple =)) I am a newbie.

---

### Post by mastablasta on 2012-08-09
what are the system specs?
 
lshw 
 
command will show them.
 
DO you have hybrid graphics? if so you need to install proprietary drivers and enable them propperly.

---

### Post by TenPlus1 on 2012-08-09
Both of these links may work, the 1st allows you to turn OFF the Radeon graphics and the 2nd lets you install Jupiter which is a nice power manager:

[http://askubuntu.com/questions/103253/how-do-i-turn-off-the-radeon-gpu-ono-my-hp-pavilion-dm4](http://askubuntu.com/questions/103253/how-do-i-turn-off-the-radeon-gpu-ono-my-hp-pavilion-dm4)

[http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html](http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html)

---

### Post by HermanAB on 2012-08-09
Another couple of points to ponder:
Your machine may have two fans and one of them may not be running.
The heat exchanger may be full of fluff.

---

### Post by marlow59 on 2012-08-09
> **TenPlus1 said:**
> Both of these links may work, the 1st allows you to turn OFF the Radeon graphics and the 2nd lets you install Jupiter which is a nice power manager:

[http://askubuntu.com/questions/103253/how-do-i-turn-off-the-radeon-gpu-ono-my-hp-pavilion-dm4](http://askubuntu.com/questions/103253/how-do-i-turn-off-the-radeon-gpu-ono-my-hp-pavilion-dm4)

[http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html](http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html)

I used to have the same problem, seems like a common problem with Optimus graphics, disabling the graphical acceleration seems to work, but for me, installing the nvidia-current driver ( sudo apt-get install nvidia-current) seems to fix the problem.

---

### Post by ruslan kim on 2012-08-09
> **mastablasta said:**
> what are the system specs?
 
lshw 
 
command will show them.
 
DO you have hybrid graphics? if so you need to install proprietary drivers and enable them propperly.



All right, I'll try from the top =))
Where do I put the "lshw" command? Sorry for the stupid question, but I am very new to Linux.

I have a sticker saying "Quad Core and Radeon Dual Graphics"...

---

### Post by NikTh on 2012-08-09
> **ruslan kim said:**
> All right, I'll try from the top =))
Where do I put the "lshw" command? Sorry for the stupid question, but I am very new to Linux.

I have a sticker saying "Quad Core and Radeon Dual Graphics"...

Hi , 
there are NO stupid questions. Nobody born learned ;)  

Open a terminal (ctrl+alt+t) and copy-paste these commands from here to terminal . One line = One command
```
sudo lshw -C video 
lspci -nnk | grep -iA2 vga
```post the results back here . 
Put the results inside [CODE] tags , by highlighting the text and click the # symbol on top of message pane.
Thanks

---

### Post by ruslan kim on 2012-08-09
```
ruslan@HP-Pavilion-g6-Notebook-PC:~$ sudo lshw -C video
PCI (sysfs)  
  *-display               
       &#1086;&#1087;&#1080;&#1089;&#1072;&#1085;&#1080;&#1077;: VGA compatible controller
       &#1087;&#1088;&#1086;&#1076;&#1091;&#1082;&#1090;: Advanced Micro Devices [AMD] nee ATI
       &#1087;&#1088;&#1086;&#1080;&#1079;&#1074;&#1086;&#1076;&#1080;&#1090;&#1077;&#1083;&#1100;: Hynix Semiconductor (Hyundai Electronics)
       &#1092;&#1080;&#1079;&#1080;&#1095;&#1077;&#1089;&#1082;&#1080;&#1081; ID: 1
       bus info: pci@0000:00:01.0
       &#1074;&#1077;&#1088;&#1089;&#1080;&#1103;: 00
       &#1088;&#1072;&#1079;&#1088;&#1103;&#1076;&#1085;&#1086;&#1089;&#1090;&#1100;: 32 bits
       &#1095;&#1072;&#1089;&#1090;&#1086;&#1090;&#1072;: 33MHz
       &#1074;&#1086;&#1079;&#1084;&#1086;&#1078;&#1085;&#1086;&#1089;&#1090;&#1080;: pm pciexpress msi vga_controller bus_master cap_list rom
       &#1082;&#1086;&#1092;&#1080;&#1075;&#1091;&#1088;&#1072;&#1094;&#1080;&#1103;: driver=radeon latency=0
       &#1088;&#1077;&#1089;&#1091;&#1088;&#1089;&#1099;: IRQ:44 &#1087;&#1072;&#1084;&#1103;&#1090;&#1100;:d0000000-dfffffff ioport:4000(size=256) &#1087;&#1072;&#1084;&#1103;&#1090;&#1100;:f0400000-f043ffff
  *-display
       &#1086;&#1087;&#1080;&#1089;&#1072;&#1085;&#1080;&#1077;: VGA compatible controller
       &#1087;&#1088;&#1086;&#1076;&#1091;&#1082;&#1090;: Seymour [Radeon HD 6400M Series]
       &#1087;&#1088;&#1086;&#1080;&#1079;&#1074;&#1086;&#1076;&#1080;&#1090;&#1077;&#1083;&#1100;: Hynix Semiconductor (Hyundai Electronics)
       &#1092;&#1080;&#1079;&#1080;&#1095;&#1077;&#1089;&#1082;&#1080;&#1081; ID: 0
       bus info: pci@0000:01:00.0
       &#1074;&#1077;&#1088;&#1089;&#1080;&#1103;: 00
       &#1088;&#1072;&#1079;&#1088;&#1103;&#1076;&#1085;&#1086;&#1089;&#1090;&#1100;: 64 bits
       &#1095;&#1072;&#1089;&#1090;&#1086;&#1090;&#1072;: 33MHz
       &#1074;&#1086;&#1079;&#1084;&#1086;&#1078;&#1085;&#1086;&#1089;&#1090;&#1080;: pm pciexpress msi vga_controller bus_master cap_list rom
       &#1082;&#1086;&#1092;&#1080;&#1075;&#1091;&#1088;&#1072;&#1094;&#1080;&#1103;: driver=radeon latency=0
       &#1088;&#1077;&#1089;&#1091;&#1088;&#1089;&#1099;: IRQ:45 &#1087;&#1072;&#1084;&#1103;&#1090;&#1100;:e0000000-efffffff &#1087;&#1072;&#1084;&#1103;&#1090;&#1100;:f0300000-f031ffff ioport:3000(size=256) &#1087;&#1072;&#1084;&#1103;&#1090;&#1100;:f0320000-f033ffff
```


```
ruslan@HP-Pavilion-g6-Notebook-PC:~$ lspci -nnk | prep -iA2 vga
&#1055;&#1088;&#1086;&#1075;&#1088;&#1072;&#1084;&#1084;&#1072; 'prep' &#1085;&#1072; &#1076;&#1072;&#1085;&#1085;&#1099;&#1081; &#1084;&#1086;&#1084;&#1077;&#1085;&#1090; &#1085;&#1077; &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1072;.  &#1042;&#1099; &#1084;&#1086;&#1078;&#1077;&#1090;&#1077; &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1080;&#1090;&#1100; &#1077;&#1105;, &#1074;&#1099;&#1087;&#1086;&#1083;&#1085;&#1080;&#1074;:
sudo apt-get install loki
```

Well, it was not hard at all =)) Here are the results. The second code says I don't have 'prep' program. Should I install it?

---

### Post by NikTh on 2012-08-09
> **ruslan kim said:**
> The second code says I don't have 'prep' program. Should I install it?

Hi , 
it is not prep ... is grep . You can copy the command from here and paste it in your terminal (for more accuracy) if you want.
```
lspci -nnk | **grep** -iA2 vga
```
Thanks

---

### Post by marlow59 on 2012-08-09
Actually, I did some researches and a lot of people are experiencing the same problem. Try to update your system, if there are any compatible new drivers for you graphic card it will maybe solve the problem. try : 

```
sudo apt-get update
      sudo apt-get upgrade

```

---

### Post by ruslan kim on 2012-08-09
> **NikTh said:**
> Hi , 
it is not prep ... is grep . You can copy the command from here and paste it in your terminal (for more accuracy) if you want.
```
lspci -nnk | **grep** -iA2 vga
```
Thanks

Thanks, you are right, I have made a mistake. So here are the results:

```
ruslan@HP-Pavilion-g6-Notebook-PC:~$ sudo lshw -C video
[sudo] password for ruslan: 
  *-display               
       &#1086;&#1087;&#1080;&#1089;&#1072;&#1085;&#1080;&#1077;: VGA compatible controller
       &#1087;&#1088;&#1086;&#1076;&#1091;&#1082;&#1090;: Advanced Micro Devices [AMD] nee ATI
       &#1087;&#1088;&#1086;&#1080;&#1079;&#1074;&#1086;&#1076;&#1080;&#1090;&#1077;&#1083;&#1100;: Hynix Semiconductor (Hyundai Electronics)
       &#1092;&#1080;&#1079;&#1080;&#1095;&#1077;&#1089;&#1082;&#1080;&#1081; ID: 1
       bus info: pci@0000:00:01.0
       &#1074;&#1077;&#1088;&#1089;&#1080;&#1103;: 00
       &#1088;&#1072;&#1079;&#1088;&#1103;&#1076;&#1085;&#1086;&#1089;&#1090;&#1100;: 32 bits
       &#1095;&#1072;&#1089;&#1090;&#1086;&#1090;&#1072;: 33MHz
       &#1074;&#1086;&#1079;&#1084;&#1086;&#1078;&#1085;&#1086;&#1089;&#1090;&#1080;: pm pciexpress msi vga_controller bus_master cap_list rom
       &#1082;&#1086;&#1092;&#1080;&#1075;&#1091;&#1088;&#1072;&#1094;&#1080;&#1103;: driver=radeon latency=0
       &#1088;&#1077;&#1089;&#1091;&#1088;&#1089;&#1099;: IRQ:43 &#1087;&#1072;&#1084;&#1103;&#1090;&#1100;:d0000000-dfffffff ioport:4000(size=256) &#1087;&#1072;&#1084;&#1103;&#1090;&#1100;:f0400000-f043ffff
  *-display
       &#1086;&#1087;&#1080;&#1089;&#1072;&#1085;&#1080;&#1077;: VGA compatible controller
       &#1087;&#1088;&#1086;&#1076;&#1091;&#1082;&#1090;: Seymour [Radeon HD 6400M Series]
       &#1087;&#1088;&#1086;&#1080;&#1079;&#1074;&#1086;&#1076;&#1080;&#1090;&#1077;&#1083;&#1100;: Hynix Semiconductor (Hyundai Electronics)
       &#1092;&#1080;&#1079;&#1080;&#1095;&#1077;&#1089;&#1082;&#1080;&#1081; ID: 0
       bus info: pci@0000:01:00.0
       &#1074;&#1077;&#1088;&#1089;&#1080;&#1103;: 00
       &#1088;&#1072;&#1079;&#1088;&#1103;&#1076;&#1085;&#1086;&#1089;&#1090;&#1100;: 64 bits
       &#1095;&#1072;&#1089;&#1090;&#1086;&#1090;&#1072;: 33MHz
       &#1074;&#1086;&#1079;&#1084;&#1086;&#1078;&#1085;&#1086;&#1089;&#1090;&#1080;: pm pciexpress msi vga_controller bus_master cap_list rom
       &#1082;&#1086;&#1092;&#1080;&#1075;&#1091;&#1088;&#1072;&#1094;&#1080;&#1103;: driver=radeon latency=0
       &#1088;&#1077;&#1089;&#1091;&#1088;&#1089;&#1099;: IRQ:45 &#1087;&#1072;&#1084;&#1103;&#1090;&#1100;:e0000000-efffffff &#1087;&#1072;&#1084;&#1103;&#1090;&#1100;:f0300000-f031ffff ioport:3000(size=256) &#1087;&#1072;&#1084;&#1103;&#1090;&#1100;:f0320000-f033ffff
ruslan@HP-Pavilion-g6-Notebook-PC:~$ lspci -nnk | grep -iA2 vga
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Device [1002:9647]
	Subsystem: Hewlett-Packard Company Device [103c:3567]
	Kernel driver in use: radeon
--
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Seymour [Radeon HD 6400M Series] [1002:6760]
	Subsystem: Hewlett-Packard Company Device [103c:3567]
	Kernel driver in use: radeon
```

---

### Post by ruslan kim on 2012-08-09
> **marlow59 said:**
> Actually, I did some researches and a lot of people are experiencing the same problem. Try to update your system, if there are any compatible new drivers for you graphic card it will maybe solve the problem. try : 

```
sudo apt-get update
      sudo apt-get upgrade

```

All right, I tried that, it seems that the system was updated:

```
ruslan@HP-Pavilion-g6-Notebook-PC:~$ sudo apt-get update
&#1048;&#1075;&#1085; http://ru.archive.ubuntu.com precise InRelease
&#1048;&#1075;&#1085; http://ru.archive.ubuntu.com precise-updates InRelease             
&#1048;&#1075;&#1085; http://ru.archive.ubuntu.com precise-backports InRelease           
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise Release.gpg                
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise-updates Release.gpg        
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise-backports Release.gpg      
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise Release                    
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise-updates Release            
&#1048;&#1075;&#1085; http://security.ubuntu.com precise-security InRelease              
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise-backports Release          
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise/main Sources               
&#1048;&#1075;&#1085; http://extras.ubuntu.com precise InRelease                         
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise/restricted Sources         
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise/universe Sources           
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise/multiverse Sources         
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise/main amd64 Packages        
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise/restricted amd64 Packages  
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise/universe amd64 Packages    
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise/multiverse amd64 Packages  
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise/main i386 Packages         
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com precise-security Release.gpg         
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise/restricted i386 Packages   
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise/universe i386 Packages     
&#1042; &#1082;&#1101;&#1096;&#1077; http://extras.ubuntu.com precise Release.gpg                    
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise/multiverse i386 Packages   
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise/main TranslationIndex      
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise/multiverse TranslationIndex
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise/restricted TranslationIndex
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise/universe TranslationIndex  
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise-updates/main Sources       
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise-updates/restricted Sources 
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise-updates/universe Sources   
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise-updates/multiverse Sources 
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com precise-security Release             
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise-updates/main amd64 Packages
&#1042; &#1082;&#1101;&#1096;&#1077; http://extras.ubuntu.com precise Release                        
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise-updates/restricted amd64 Packages
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise-updates/universe amd64 Packages
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise-updates/multiverse amd64 Packages
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise-updates/main i386 Packages 
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise-updates/restricted i386 Packages
&#1048;&#1075;&#1085; http://linux.dropbox.com precise InRelease                         
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise-updates/universe i386 Packages
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise-updates/multiverse i386 Packages
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise-updates/main TranslationIndex
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise-updates/multiverse TranslationIndex
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise-updates/restricted TranslationIndex
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com precise-security/main Sources        
&#1042; &#1082;&#1101;&#1096;&#1077; http://extras.ubuntu.com precise/main Sources                   
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise-updates/universe TranslationIndex
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise-backports/main Sources     
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise-backports/restricted Sources
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise-backports/universe Sources 
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise-backports/multiverse Sources
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise-backports/main amd64 Packages
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise-backports/restricted amd64 Packages
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise-backports/universe amd64 Packages
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise-backports/multiverse amd64 Packages
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise-backports/main i386 Packages
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise-backports/restricted i386 Packages
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com precise-security/restricted Sources  
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com precise-security/universe Sources    
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com precise-security/multiverse Sources  
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com precise-security/main amd64 Packages 
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com precise-security/restricted amd64 Packages
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise-backports/universe i386 Packages
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise-backports/multiverse i386 Packages
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com precise-security/universe amd64 Packages
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com precise-security/multiverse amd64 Packages
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com precise-security/main i386 Packages  
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com precise-security/restricted i386 Packages
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com precise-security/universe i386 Packages
&#1042; &#1082;&#1101;&#1096;&#1077; http://linux.dropbox.com precise Release.gpg                    
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise-backports/main TranslationIndex
&#1042; &#1082;&#1101;&#1096;&#1077; http://extras.ubuntu.com precise/main amd64 Packages            
&#1042; &#1082;&#1101;&#1096;&#1077; http://extras.ubuntu.com precise/main i386 Packages             
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise-backports/multiverse TranslationIndex
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise-backports/restricted TranslationIndex
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise-backports/universe TranslationIndex
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise/main Translation-ru        
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise/main Translation-en        
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise/multiverse Translation-ru  
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise/multiverse Translation-en  
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise/restricted Translation-ru  
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise/restricted Translation-en  
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise/universe Translation-ru    
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise/universe Translation-en    
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com precise-security/multiverse i386 Packages
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com precise-security/main TranslationIndex
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com precise-security/multiverse TranslationIndex
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com precise-security/restricted TranslationIndex
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com precise-security/universe TranslationIndex
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise-updates/main Translation-ru
&#1048;&#1075;&#1085; http://extras.ubuntu.com precise/main TranslationIndex             
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise-updates/main Translation-en
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise-updates/multiverse Translation-ru
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise-updates/multiverse Translation-en
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise-updates/restricted Translation-ru
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise-updates/restricted Translation-en
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise-updates/universe Translation-ru
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise-updates/universe Translation-en
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise-backports/main Translation-en
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise-backports/multiverse Translation-en
&#1042; &#1082;&#1101;&#1096;&#1077; http://linux.dropbox.com precise Release                        
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise-backports/restricted Translation-en
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com precise-security/main Translation-en 
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com precise-security/multiverse Translation-en
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com precise-security/restricted Translation-en
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com precise-backports/universe Translation-en
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com precise-security/universe Translation-en
&#1042; &#1082;&#1101;&#1096;&#1077; http://linux.dropbox.com precise/main amd64 Packages            
&#1042; &#1082;&#1101;&#1096;&#1077; http://linux.dropbox.com precise/main i386 Packages             
&#1048;&#1075;&#1085; http://linux.dropbox.com precise/main TranslationIndex             
&#1048;&#1075;&#1085; http://extras.ubuntu.com precise/main Translation-ru_RU            
&#1048;&#1075;&#1085; http://extras.ubuntu.com precise/main Translation-ru
&#1048;&#1075;&#1085; http://extras.ubuntu.com precise/main Translation-en
&#1048;&#1075;&#1085; http://linux.dropbox.com precise/main Translation-ru_RU
&#1048;&#1075;&#1085; http://linux.dropbox.com precise/main Translation-ru
&#1048;&#1075;&#1085; http://linux.dropbox.com precise/main Translation-en
&#1063;&#1090;&#1077;&#1085;&#1080;&#1077; &#1089;&#1087;&#1080;&#1089;&#1082;&#1086;&#1074; &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074;… &#1043;&#1086;&#1090;&#1086;&#1074;&#1086;
ruslan@HP-Pavilion-g6-Notebook-PC:~$ sudo apt-get upgrade
&#1063;&#1090;&#1077;&#1085;&#1080;&#1077; &#1089;&#1087;&#1080;&#1089;&#1082;&#1086;&#1074; &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074;… &#1043;&#1086;&#1090;&#1086;&#1074;&#1086;
&#1055;&#1086;&#1089;&#1090;&#1088;&#1086;&#1077;&#1085;&#1080;&#1077; &#1076;&#1077;&#1088;&#1077;&#1074;&#1072; &#1079;&#1072;&#1074;&#1080;&#1089;&#1080;&#1084;&#1086;&#1089;&#1090;&#1077;&#1081;       
&#1063;&#1090;&#1077;&#1085;&#1080;&#1077; &#1080;&#1085;&#1092;&#1086;&#1088;&#1084;&#1072;&#1094;&#1080;&#1080; &#1086; &#1089;&#1086;&#1089;&#1090;&#1086;&#1103;&#1085;&#1080;&#1080;… &#1043;&#1086;&#1090;&#1086;&#1074;&#1086;
&#1055;&#1072;&#1082;&#1077;&#1090;&#1099;, &#1082;&#1086;&#1090;&#1086;&#1088;&#1099;&#1077; &#1073;&#1091;&#1076;&#1091;&#1090; &#1086;&#1089;&#1090;&#1072;&#1074;&#1083;&#1077;&#1085;&#1099; &#1074; &#1085;&#1077;&#1080;&#1079;&#1084;&#1077;&#1085;&#1085;&#1086;&#1084; &#1074;&#1080;&#1076;&#1077;:
  linux-generic linux-headers-generic linux-image-generic
&#1055;&#1072;&#1082;&#1077;&#1090;&#1099;, &#1082;&#1086;&#1090;&#1086;&#1088;&#1099;&#1077; &#1073;&#1091;&#1076;&#1091;&#1090; &#1086;&#1073;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1099;:
  language-pack-en language-pack-en-base language-pack-gnome-en
  language-pack-gnome-en-base libfreerdp-plugins-standard libfreerdp1
  linux-libc-dev software-center unity-greeter
&#1086;&#1073;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1086; 9, &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1086; 0 &#1085;&#1086;&#1074;&#1099;&#1093; &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074;, &#1076;&#1083;&#1103; &#1091;&#1076;&#1072;&#1083;&#1077;&#1085;&#1080;&#1103; &#1086;&#1090;&#1084;&#1077;&#1095;&#1077;&#1085;&#1086; 0 &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074;, &#1080; 3 &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074; &#1085;&#1077; &#1086;&#1073;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1086;.
&#1053;&#1077;&#1086;&#1073;&#1093;&#1086;&#1076;&#1080;&#1084;&#1086; &#1089;&#1082;&#1072;&#1095;&#1072;&#1090;&#1100; 4*135 k&#1041; &#1072;&#1088;&#1093;&#1080;&#1074;&#1086;&#1074;.
&#1055;&#1086;&#1089;&#1083;&#1077; &#1076;&#1072;&#1085;&#1085;&#1086;&#1081; &#1086;&#1087;&#1077;&#1088;&#1072;&#1094;&#1080;&#1080;, &#1086;&#1073;&#1098;&#1105;&#1084; &#1079;&#1072;&#1085;&#1103;&#1090;&#1086;&#1075;&#1086; &#1076;&#1080;&#1089;&#1082;&#1086;&#1074;&#1086;&#1075;&#1086; &#1087;&#1088;&#1086;&#1089;&#1090;&#1088;&#1072;&#1085;&#1089;&#1090;&#1074;&#1072; &#1091;&#1084;&#1077;&#1085;&#1100;&#1096;&#1080;&#1090;&#1089;&#1103; &#1085;&#1072; 2*419 kB.
&#1061;&#1086;&#1090;&#1080;&#1090;&#1077; &#1087;&#1088;&#1086;&#1076;&#1086;&#1083;&#1078;&#1080;&#1090;&#1100; [&#1044;/&#1085;]? y
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:1 http://ru.archive.ubuntu.com/ubuntu/ precise-updates/main language-pack-en all 1:12.04+20120801 [1*994 B]
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:2 http://ru.archive.ubuntu.com/ubuntu/ precise-updates/main language-pack-en-base all 1:12.04+20120801 [878 kB]
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:3 http://security.ubuntu.com/ubuntu/ precise-security/main linux-libc-dev amd64 3.2.0-29.46 [871 kB]
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:4 http://ru.archive.ubuntu.com/ubuntu/ precise-updates/main language-pack-gnome-en all 1:12.04+20120801 [2*018 B]
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:5 http://ru.archive.ubuntu.com/ubuntu/ precise-updates/main language-pack-gnome-en-base all 1:12.04+20120801 [1*356 kB]
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:6 http://ru.archive.ubuntu.com/ubuntu/ precise-updates/main libfreerdp1 amd64 1.0.1-1ubuntu2.1 [242 kB]
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:7 http://ru.archive.ubuntu.com/ubuntu/ precise-updates/main libfreerdp-plugins-standard amd64 1.0.1-1ubuntu2.1 [73,9 kB]
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:8 http://ru.archive.ubuntu.com/ubuntu/ precise-updates/main software-center all 5.2.5 [624 kB]
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086;:9 http://ru.archive.ubuntu.com/ubuntu/ precise-updates/main unity-greeter amd64 0.2.8-0ubuntu1.2 [85,2 kB]
&#1055;&#1086;&#1083;&#1091;&#1095;&#1077;&#1085;&#1086; 4*135 k&#1041; &#1079;&#1072; 6&#1089; (627 k&#1041;/c)                                     
(&#1063;&#1090;&#1077;&#1085;&#1080;&#1077; &#1073;&#1072;&#1079;&#1099; &#1076;&#1072;&#1085;&#1085;&#1099;&#1093; ... &#1085;&#1072; &#1076;&#1072;&#1085;&#1085;&#1099;&#1081; &#1084;&#1086;&#1084;&#1077;&#1085;&#1090; &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1086; 184629 &#1092;&#1072;&#1081;&#1083;&#1086;&#1074; &#1080; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075;&#1086;&#1074;.)
&#1055;&#1086;&#1076;&#1075;&#1086;&#1090;&#1086;&#1074;&#1082;&#1072; &#1082; &#1079;&#1072;&#1084;&#1077;&#1085;&#1077; &#1087;&#1072;&#1082;&#1077;&#1090;&#1072; language-pack-en 1:12.04+20120618 (&#1080;&#1089;&#1087;&#1086;&#1083;&#1100;&#1079;&#1091;&#1077;&#1090;&#1089;&#1103; &#1092;&#1072;&#1081;&#1083; .../language-pack-en_1%3a12.04+20120801_all.deb) ...
&#1056;&#1072;&#1089;&#1087;&#1072;&#1082;&#1086;&#1074;&#1099;&#1074;&#1072;&#1077;&#1090;&#1089;&#1103; &#1079;&#1072;&#1084;&#1077;&#1085;&#1072; &#1076;&#1083;&#1103; &#1087;&#1072;&#1082;&#1077;&#1090;&#1072; language-pack-en ...
&#1055;&#1086;&#1076;&#1075;&#1086;&#1090;&#1086;&#1074;&#1082;&#1072; &#1082; &#1079;&#1072;&#1084;&#1077;&#1085;&#1077; &#1087;&#1072;&#1082;&#1077;&#1090;&#1072; language-pack-en-base 1:12.04+20120508 (&#1080;&#1089;&#1087;&#1086;&#1083;&#1100;&#1079;&#1091;&#1077;&#1090;&#1089;&#1103; &#1092;&#1072;&#1081;&#1083; .../language-pack-en-base_1%3a12.04+20120801_all.deb) ...
&#1056;&#1072;&#1089;&#1087;&#1072;&#1082;&#1086;&#1074;&#1099;&#1074;&#1072;&#1077;&#1090;&#1089;&#1103; &#1079;&#1072;&#1084;&#1077;&#1085;&#1072; &#1076;&#1083;&#1103; &#1087;&#1072;&#1082;&#1077;&#1090;&#1072; language-pack-en-base ...
&#1055;&#1086;&#1076;&#1075;&#1086;&#1090;&#1086;&#1074;&#1082;&#1072; &#1082; &#1079;&#1072;&#1084;&#1077;&#1085;&#1077; &#1087;&#1072;&#1082;&#1077;&#1090;&#1072; language-pack-gnome-en 1:12.04+20120618 (&#1080;&#1089;&#1087;&#1086;&#1083;&#1100;&#1079;&#1091;&#1077;&#1090;&#1089;&#1103; &#1092;&#1072;&#1081;&#1083; .../language-pack-gnome-en_1%3a12.04+20120801_all.deb) ...
&#1056;&#1072;&#1089;&#1087;&#1072;&#1082;&#1086;&#1074;&#1099;&#1074;&#1072;&#1077;&#1090;&#1089;&#1103; &#1079;&#1072;&#1084;&#1077;&#1085;&#1072; &#1076;&#1083;&#1103; &#1087;&#1072;&#1082;&#1077;&#1090;&#1072; language-pack-gnome-en ...
&#1055;&#1086;&#1076;&#1075;&#1086;&#1090;&#1086;&#1074;&#1082;&#1072; &#1082; &#1079;&#1072;&#1084;&#1077;&#1085;&#1077; &#1087;&#1072;&#1082;&#1077;&#1090;&#1072; language-pack-gnome-en-base 1:12.04+20120508 (&#1080;&#1089;&#1087;&#1086;&#1083;&#1100;&#1079;&#1091;&#1077;&#1090;&#1089;&#1103; &#1092;&#1072;&#1081;&#1083; .../language-pack-gnome-en-base_1%3a12.04+20120801_all.deb) ...
&#1056;&#1072;&#1089;&#1087;&#1072;&#1082;&#1086;&#1074;&#1099;&#1074;&#1072;&#1077;&#1090;&#1089;&#1103; &#1079;&#1072;&#1084;&#1077;&#1085;&#1072; &#1076;&#1083;&#1103; &#1087;&#1072;&#1082;&#1077;&#1090;&#1072; language-pack-gnome-en-base ...
&#1055;&#1086;&#1076;&#1075;&#1086;&#1090;&#1086;&#1074;&#1082;&#1072; &#1082; &#1079;&#1072;&#1084;&#1077;&#1085;&#1077; &#1087;&#1072;&#1082;&#1077;&#1090;&#1072; libfreerdp1 1.0.1-1ubuntu2 (&#1080;&#1089;&#1087;&#1086;&#1083;&#1100;&#1079;&#1091;&#1077;&#1090;&#1089;&#1103; &#1092;&#1072;&#1081;&#1083; .../libfreerdp1_1.0.1-1ubuntu2.1_amd64.deb) ...
&#1056;&#1072;&#1089;&#1087;&#1072;&#1082;&#1086;&#1074;&#1099;&#1074;&#1072;&#1077;&#1090;&#1089;&#1103; &#1079;&#1072;&#1084;&#1077;&#1085;&#1072; &#1076;&#1083;&#1103; &#1087;&#1072;&#1082;&#1077;&#1090;&#1072; libfreerdp1 ...
&#1055;&#1086;&#1076;&#1075;&#1086;&#1090;&#1086;&#1074;&#1082;&#1072; &#1082; &#1079;&#1072;&#1084;&#1077;&#1085;&#1077; &#1087;&#1072;&#1082;&#1077;&#1090;&#1072; libfreerdp-plugins-standard 1.0.1-1ubuntu2 (&#1080;&#1089;&#1087;&#1086;&#1083;&#1100;&#1079;&#1091;&#1077;&#1090;&#1089;&#1103; &#1092;&#1072;&#1081;&#1083; .../libfreerdp-plugins-standard_1.0.1-1ubuntu2.1_amd64.deb) ...
&#1056;&#1072;&#1089;&#1087;&#1072;&#1082;&#1086;&#1074;&#1099;&#1074;&#1072;&#1077;&#1090;&#1089;&#1103; &#1079;&#1072;&#1084;&#1077;&#1085;&#1072; &#1076;&#1083;&#1103; &#1087;&#1072;&#1082;&#1077;&#1090;&#1072; libfreerdp-plugins-standard ...
&#1055;&#1086;&#1076;&#1075;&#1086;&#1090;&#1086;&#1074;&#1082;&#1072; &#1082; &#1079;&#1072;&#1084;&#1077;&#1085;&#1077; &#1087;&#1072;&#1082;&#1077;&#1090;&#1072; linux-libc-dev 3.2.0-27.43 (&#1080;&#1089;&#1087;&#1086;&#1083;&#1100;&#1079;&#1091;&#1077;&#1090;&#1089;&#1103; &#1092;&#1072;&#1081;&#1083; .../linux-libc-dev_3.2.0-29.46_amd64.deb) ...
&#1056;&#1072;&#1089;&#1087;&#1072;&#1082;&#1086;&#1074;&#1099;&#1074;&#1072;&#1077;&#1090;&#1089;&#1103; &#1079;&#1072;&#1084;&#1077;&#1085;&#1072; &#1076;&#1083;&#1103; &#1087;&#1072;&#1082;&#1077;&#1090;&#1072; linux-libc-dev ...
&#1055;&#1086;&#1076;&#1075;&#1086;&#1090;&#1086;&#1074;&#1082;&#1072; &#1082; &#1079;&#1072;&#1084;&#1077;&#1085;&#1077; &#1087;&#1072;&#1082;&#1077;&#1090;&#1072; software-center 5.2.4 (&#1080;&#1089;&#1087;&#1086;&#1083;&#1100;&#1079;&#1091;&#1077;&#1090;&#1089;&#1103; &#1092;&#1072;&#1081;&#1083; .../software-center_5.2.5_all.deb) ...
&#1056;&#1072;&#1089;&#1087;&#1072;&#1082;&#1086;&#1074;&#1099;&#1074;&#1072;&#1077;&#1090;&#1089;&#1103; &#1079;&#1072;&#1084;&#1077;&#1085;&#1072; &#1076;&#1083;&#1103; &#1087;&#1072;&#1082;&#1077;&#1090;&#1072; software-center ...
&#1055;&#1086;&#1076;&#1075;&#1086;&#1090;&#1086;&#1074;&#1082;&#1072; &#1082; &#1079;&#1072;&#1084;&#1077;&#1085;&#1077; &#1087;&#1072;&#1082;&#1077;&#1090;&#1072; unity-greeter 0.2.8-0ubuntu1.1 (&#1080;&#1089;&#1087;&#1086;&#1083;&#1100;&#1079;&#1091;&#1077;&#1090;&#1089;&#1103; &#1092;&#1072;&#1081;&#1083; .../unity-greeter_0.2.8-0ubuntu1.2_amd64.deb) ...
&#1056;&#1072;&#1089;&#1087;&#1072;&#1082;&#1086;&#1074;&#1099;&#1074;&#1072;&#1077;&#1090;&#1089;&#1103; &#1079;&#1072;&#1084;&#1077;&#1085;&#1072; &#1076;&#1083;&#1103; &#1087;&#1072;&#1082;&#1077;&#1090;&#1072; unity-greeter ...
&#1054;&#1073;&#1088;&#1072;&#1073;&#1072;&#1090;&#1099;&#1074;&#1072;&#1102;&#1090;&#1089;&#1103; &#1090;&#1088;&#1080;&#1075;&#1075;&#1077;&#1088;&#1099; &#1076;&#1083;&#1103; man-db ...
&#1054;&#1073;&#1088;&#1072;&#1073;&#1072;&#1090;&#1099;&#1074;&#1072;&#1102;&#1090;&#1089;&#1103; &#1090;&#1088;&#1080;&#1075;&#1075;&#1077;&#1088;&#1099; &#1076;&#1083;&#1103; hicolor-icon-theme ...
&#1054;&#1073;&#1088;&#1072;&#1073;&#1072;&#1090;&#1099;&#1074;&#1072;&#1102;&#1090;&#1089;&#1103; &#1090;&#1088;&#1080;&#1075;&#1075;&#1077;&#1088;&#1099; &#1076;&#1083;&#1103; bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
&#1054;&#1073;&#1088;&#1072;&#1073;&#1072;&#1090;&#1099;&#1074;&#1072;&#1102;&#1090;&#1089;&#1103; &#1090;&#1088;&#1080;&#1075;&#1075;&#1077;&#1088;&#1099; &#1076;&#1083;&#1103; desktop-file-utils ...
&#1054;&#1073;&#1088;&#1072;&#1073;&#1072;&#1090;&#1099;&#1074;&#1072;&#1102;&#1090;&#1089;&#1103; &#1090;&#1088;&#1080;&#1075;&#1075;&#1077;&#1088;&#1099; &#1076;&#1083;&#1103; gnome-menus ...
&#1054;&#1073;&#1088;&#1072;&#1073;&#1072;&#1090;&#1099;&#1074;&#1072;&#1102;&#1090;&#1089;&#1103; &#1090;&#1088;&#1080;&#1075;&#1075;&#1077;&#1088;&#1099; &#1076;&#1083;&#1103; libglib2.0-0 ...
&#1053;&#1072;&#1089;&#1090;&#1088;&#1072;&#1080;&#1074;&#1072;&#1077;&#1090;&#1089;&#1103; &#1087;&#1072;&#1082;&#1077;&#1090; libfreerdp1 (1.0.1-1ubuntu2.1) ...
&#1053;&#1072;&#1089;&#1090;&#1088;&#1072;&#1080;&#1074;&#1072;&#1077;&#1090;&#1089;&#1103; &#1087;&#1072;&#1082;&#1077;&#1090; libfreerdp-plugins-standard (1.0.1-1ubuntu2.1) ...
&#1053;&#1072;&#1089;&#1090;&#1088;&#1072;&#1080;&#1074;&#1072;&#1077;&#1090;&#1089;&#1103; &#1087;&#1072;&#1082;&#1077;&#1090; linux-libc-dev (3.2.0-29.46) ...
&#1053;&#1072;&#1089;&#1090;&#1088;&#1072;&#1080;&#1074;&#1072;&#1077;&#1090;&#1089;&#1103; &#1087;&#1072;&#1082;&#1077;&#1090; software-center (5.2.5) ...
Updating software catalog...this may take a moment.
INFO:softwarecenter.db.pkginfo_impl.aptcache:aptcache.open()
Software catalog update was successful.
&#1053;&#1072;&#1089;&#1090;&#1088;&#1072;&#1080;&#1074;&#1072;&#1077;&#1090;&#1089;&#1103; &#1087;&#1072;&#1082;&#1077;&#1090; unity-greeter (0.2.8-0ubuntu1.2) ...
&#1053;&#1072;&#1089;&#1090;&#1088;&#1072;&#1080;&#1074;&#1072;&#1077;&#1090;&#1089;&#1103; &#1087;&#1072;&#1082;&#1077;&#1090; language-pack-en (1:12.04+20120801) ...
&#1053;&#1072;&#1089;&#1090;&#1088;&#1072;&#1080;&#1074;&#1072;&#1077;&#1090;&#1089;&#1103; &#1087;&#1072;&#1082;&#1077;&#1090; language-pack-en-base (1:12.04+20120801) ...
Generating locales...
  en_AG.UTF-8... done
  en_AU.UTF-8... done
  en_BW.UTF-8... done
  en_CA.UTF-8... done
  en_DK.UTF-8... done
  en_GB.UTF-8... done
  en_HK.UTF-8... done
  en_IE.UTF-8... done
  en_IN.UTF-8... done
  en_NG.UTF-8... done
  en_NZ.UTF-8... done
  en_PH.UTF-8... done
  en_SG.UTF-8... done
  en_US.UTF-8... done
  en_ZA.UTF-8... done
  en_ZM.UTF-8... done
  en_ZW.UTF-8... done
Generation complete.
&#1053;&#1072;&#1089;&#1090;&#1088;&#1072;&#1080;&#1074;&#1072;&#1077;&#1090;&#1089;&#1103; &#1087;&#1072;&#1082;&#1077;&#1090; language-pack-gnome-en (1:12.04+20120801) ...
&#1053;&#1072;&#1089;&#1090;&#1088;&#1072;&#1080;&#1074;&#1072;&#1077;&#1090;&#1089;&#1103; &#1087;&#1072;&#1082;&#1077;&#1090; language-pack-gnome-en-base (1:12.04+20120801) ...
&#1054;&#1073;&#1088;&#1072;&#1073;&#1072;&#1090;&#1099;&#1074;&#1072;&#1102;&#1090;&#1089;&#1103; &#1090;&#1088;&#1080;&#1075;&#1075;&#1077;&#1088;&#1099; &#1076;&#1083;&#1103; libc-bin ...
ldconfig deferred processing now taking place
&#1054;&#1073;&#1088;&#1072;&#1073;&#1072;&#1090;&#1099;&#1074;&#1072;&#1102;&#1090;&#1089;&#1103; &#1090;&#1088;&#1080;&#1075;&#1075;&#1077;&#1088;&#1099; &#1076;&#1083;&#1103; bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
```

---

### Post by ruslan kim on 2012-08-09
> **TenPlus1 said:**
> Both of these links may work, the 1st allows you to turn OFF the Radeon graphics and the 2nd lets you install Jupiter which is a nice power manager:

[http://askubuntu.com/questions/103253/how-do-i-turn-off-the-radeon-gpu-ono-my-hp-pavilion-dm4](http://askubuntu.com/questions/103253/how-do-i-turn-off-the-radeon-gpu-ono-my-hp-pavilion-dm4)

[http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html](http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html)

I tried to install Jupiter:

```
ruslan@HP-Pavilion-g6-Notebook-PC:~$ sudo add-apt-repository ppa:webupd8team/jupiter
You are about to add the following PPA to your system:
 Jupiter: http://sourceforge.net/projects/jupiter/files/

More info: http://www.webupd8.org/2010/07/jupiter-ubuntu-ppa-hardware-and-power.html
 More info: https://launchpad.net/~webupd8team/+archive/jupiter
Press [ENTER] to continue or ctrl-c to cancel adding it

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.zMJ9LP0QGT --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 7B2C3B0889BF5709A105D03AC2518248EEA14886
gpg: &#1079;&#1072;&#1087;&#1088;&#1072;&#1096;&#1080;&#1074;&#1072;&#1102; &#1082;&#1083;&#1102;&#1095; EEA14886 &#1089; hkp &#1089;&#1077;&#1088;&#1074;&#1077;&#1088;&#1072; keyserver.ubuntu.com
gpg: &#1082;&#1083;&#1102;&#1095; EEA14886: &#1086;&#1090;&#1082;&#1088;&#1099;&#1090;&#1099;&#1081; &#1082;&#1083;&#1102;&#1095; "Launchpad VLC" &#1080;&#1084;&#1087;&#1086;&#1088;&#1090;&#1080;&#1088;&#1086;&#1074;&#1072;&#1085;
gpg: &#1042;&#1089;&#1077;&#1075;&#1086; &#1086;&#1073;&#1088;&#1072;&#1073;&#1086;&#1090;&#1072;&#1085;&#1086;: 1
gpg:               &#1080;&#1084;&#1087;&#1086;&#1088;&#1090;&#1080;&#1088;&#1086;&#1074;&#1072;&#1085;&#1086;: 1  (RSA: 1)
```

Seems to be installed, but where I can find it?

---

### Post by jonnyboysmithy on 2012-08-09
> **ruslan kim said:**
> Seems to be installed, but where I can find it?
You can run ```
jupiter
``` from the terminal. I would add a startup entry. Search for startup applications then click the Add button, give it a name: jupiter Command to run: jupiter and some comment if you want to be really tidy ;)
And you're done! :)

---

### Post by ruslan kim on 2012-08-10
> **jonnyboysmithy said:**
> You can run ```
jupiter
``` from the terminal. I would add a startup entry. Search for startup applications then click the Add button, give it a name: jupiter Command to run: jupiter and some comment if you want to be really tidy ;)
And you're done! :)

It seems that the program wasn't installed:
```
ruslan@HP-Pavilion-g6-Notebook-PC:~$ jupiter
jupiter: command not found
```
How to install it properly? Pls see how I tried to install it in the previous posts.

---

### Post by simonmoon42 on 2012-08-10
Did you run: 
```
sudo apt-get install jupiter
```

If you didn't... all you did is at the ppa to your list. After you add the PPA then you still need to install the software.

---

### Post by Gone fishing on 2012-08-10
I've had problems with my laptop overheating and then shutting down. After experimenting I found this line: 

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash thermal.off=1 acpi_osi="
``` in /etc/default/grub followed by ```
sudo update-grub
``` seemed to fix the problem. I think it gives full control of the fans to system BIOS rather than the Linux kernel, anyway the fans seem to be spinning as they should - however, I also blew out the system so that might have helped too.

I also installed temp sensors in conkey so I could see whats happening at the moment one core is running at 38C the other 44C

---

### Post by ruslan kim on 2012-08-10
> **jonnyboysmithy said:**
> You can run ```
jupiter
``` from the terminal. I would add a startup entry. Search for startup applications then click the Add button, give it a name: jupiter Command to run: jupiter and some comment if you want to be really tidy ;)
And you're done! :)

> **simonmoon42 said:**
> Did you run: 
```
sudo apt-get install jupiter
```

If you didn't... all you did is at the ppa to your list. After you add the PPA then you still need to install the software.


Finally I installed it! =) And when I type

```
jupiter
```

in the terminal this what happens:

```
ruslan@HP-Pavilion-g6-Notebook-PC:~$ jupiter
[sudo] password for ruslan: 
Exception in thread Thread-4:
Traceback (most recent call last):
  File "/usr/lib/python2.7/threading.py", line 551, in __bootstrap_inner
    self.run()
  File "/usr/lib/python2.7/threading.py", line 504, in run
    self.__target(*self.__args, **self.__kwargs)
  File "/usr/bin/jupiter", line 411, in update_screen_resolutions
    res = self.jupiter.get_available_resolutions(display)
  File "/usr/bin/jupiter", line 180, in get_available_resolutions
    return self.get_device('/available_resolutions_' + args,'resolutions','modes ' + args).split(' ')
AttributeError: 'bool' object has no attribute 'split'

Exception in thread Thread-5:
Traceback (most recent call last):
  File "/usr/lib/python2.7/threading.py", line 551, in __bootstrap_inner
    self.run()
  File "/usr/lib/python2.7/threading.py", line 504, in run
    self.__target(*self.__args, **self.__kwargs)
  File "/usr/bin/jupiter", line 379, in update_screen_orientations
    rotation = self.jupiter.current_rotation(display)
  File "/usr/bin/jupiter", line 165, in current_rotation
    return self.get_device('/rotation_saved_'+args, 'rotate', ['normal',args]).split(' ')[0]
AttributeError: 'bool' object has no attribute 'split'
```

Now Jupiter seems to work... The CPU temp is 60 degrees. Is it high or not? What is the max temp that a CPU can stand?

---

### Post by ruslan kim on 2012-08-10
> **Gone fishing said:**
> I've had problems with my laptop overheating and then shutting down. After experimenting I found this line: 

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash thermal.off=1 acpi_osi="
``` in /etc/default/grub followed by ```
sudo update-grub
``` seemed to fix the problem. I think it gives full control of the fans to system BIOS rather than the Linux kernel, anyway the fans seem to be spinning as they should - however, I also blew out the system so that might have helped too.

I also installed temp sensors in conkey so I could see whats happening at the moment one core is running at 38C the other 44C

Can you please explain that step-by-step? Btw, according to Jupiter my CPU temp is 60 now(

---

### Post by ruslan kim on 2012-08-10
> **ruslan kim said:**
> Can you please explain that step-by-step? Btw, according to Jupiter my CPU temp is 60 now(

And how did you install temp sensors in conkey?

---

### Post by simonmoon42 on 2012-08-10
> **ruslan kim said:**
> Now Jupiter seems to work... The CPU temp is 60 degrees. Is it high or not? What is the max temp that a CPU can stand?

While 60 is a bit on the high side, the maximum temp for your CPU is 90c so it shouldn't be an issue.

---

### Post by Gone fishing on 2012-08-10
Sorry

open a terminal and run ```
gksu gedit /etc/default/grub
```look for the line GRUB_CMDLINE_LINUX_DEFAULT and change it so that it looks like ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash thermal.off=1 acpi_osi="
``` Then run ```
sudo update-grub
```. Then reboot

My conky temp looks like 

```
Temperature

Core 0 Temp: ${execi 8 sensors | grep 'Core0' | paste -s |sed 's/°/\n/'| head -n1 | cut -c15-} C
Core 1 Temp: ${execi 8 sensors | grep 'Core1' | paste -s |sed 's/°/\n/'| head -n1 | cut -c15-} C
```

---

### Post by ruslan kim on 2012-08-11
> **Gone fishing said:**
> Sorry

open a terminal and run ```
gksu gedit /etc/default/grub
```look for the line GRUB_CMDLINE_LINUX_DEFAULT and change it so that it looks like ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash thermal.off=1 acpi_osi="
``` Then run ```
sudo update-grub
```. Then reboot

My conky temp looks like 

```
Temperature

Core 0 Temp: ${execi 8 sensors | grep 'Core0' | paste -s |sed 's/°/\n/'| head -n1 | cut -c15-} C
Core 1 Temp: ${execi 8 sensors | grep 'Core1' | paste -s |sed 's/°/\n/'| head -n1 | cut -c15-} C
```

What do I do with this conky temp? Insert in the terminal?

BTW, the CPU seems to cool after I did what you suggested. According to Jupiter it is about 52-53 degrees now.

---

### Post by Gone fishing on 2012-08-11
no just open the /home/username/.conkyrc file and add to the bottom. ```
gedit /home/username/.conkyrc
``` then run conky from a terminal to check if it gives any errors I think you need to install lm-sensors.
```
sudo apt-get install lm-sensors
```

Ther is a good conky thread in community cafe with examples of cofig files etc

---

### Post by ruslan kim on 2012-08-11
> **Gone fishing said:**
> no just open the /home/username/.conkyrc file and add to the bottom. ```
gedit /home/username/.conkyrc
``` then run conky from a terminal to check if it gives any errors I think you need to install lm-sensors.
```
sudo apt-get install lm-sensors
```

Ther is a good conky thread in community cafe with examples of cofig files etc

I can't. I open "home", there is only one directory "ruslan", I click it and I see My Videos, Pictures, Downloads, Music, etc. I think it is not the place)) Where is it?

---

### Post by Gone fishing on 2012-08-11
> I can't. I open "home", there is only one directory "ruslan", I click it and I see My Videos, Pictures, Downloads, Music, etc. I think it is not the place)) Where is it?

It is there! In your case /home/ruslan If you open nautilus and click file system you will see /home /etc etc. Inside /home you will see ruslan. To see hidden files which are named .filename you need to go to view and select Show hidden files.

However, to get conky working have a look at this 

[http://ubuntuforums.org/showthread.php?t=1644427](http://ubuntuforums.org/showthread.php?t=1644427)

[https://help.ubuntu.com/community/SettingUpConky](https://help.ubuntu.com/community/SettingUpConky)

---

### Post by ruslan kim on 2012-08-11
The problem is solved!

What I did is simple - I just reinstall Ubuntu 12.04 from the very beginning. I wanted to change the language to English anyway. During the installation I installed additional drivers for my graphics card (I remember I didn't manage to do it during the previous installation process).
Now everything works pretty well, so I suppose the problem was in the graphic card.

Many thanks everybody for the help and have a nice day! ;)

---

