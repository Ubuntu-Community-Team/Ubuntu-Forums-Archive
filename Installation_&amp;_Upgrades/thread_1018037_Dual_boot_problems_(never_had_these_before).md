---
title: "Dual boot problems (never had these before)"
date: 2008-12-21
forum: Installation &amp; Upgrades
---

### Post by Moonfrost on 2008-12-21
I was trying to make a dual boot of Kubuntu 8.10 and Windows XP (Kubuntu installed first) and I followed the normal procedures (I have done this a million times) up to where I have to boot into the Ubuntu live disc (because at this point I just installed XP and only XP is bootable so I have to go into the Ubuntu live disc to restore grub) and when I go into terminal and type:

```
root (hd0,0)
``` (I only have one single 500gb drive)

and then I type:

```
setup (hd0)
``` I get error 17, I have never had this problem so I don't understand what's going on, I tried a few things but none of them worked.

So as a last resort I went to Partition Editor and set the main Kubuntu partition as "boot" (while removing it from the Windows partition) and now Kubuntu boots but Windows doesn't.

So I went into a terminal and typed:

```
kdesudo kate /boot/grub/menu.lst
``` in gnome that used to be:

```
sudo gedit /boot/grub/menu.lst
```

Kate opened up the file no problem as always and I put the Windows XP entry in it as usual like this:
```

title          Windows XP
root           (hd0,1)
makeactive
chainloader +1
```

But that didn't seem to work, when I restart the system and press escape to go into the grub menu I choose "Windows XP" and the grub timeout appears again and I press escape again and all the options appear again. So I don't know any way I can still boot into Windows...anybody know what might have gone wrong? do I have to re-install any of the OSs? I HOPE NOT! but if I have to oh well...anyway can anybody help (and sorry this is so long but I'm trying to be as detailed as possible)?

---

### Post by zvacet on 2008-12-21
Read [this]("http://users.bigpond.net.au/hermanzone/p15.htm#17") and I hope it will be helpful to you.

---

### Post by ebmelle on 2008-12-21
Suggest, while able to boot Windows XP, reinstall Ubuntu, and chances are both will boot AOK when selected.  Ubuntu seems to have mastered the dual boot with Windows installed fine, but MS Windows never made the effort to enable dual boot if any other OS was previously installed.:)

---

### Post by caljohnsmith on 2008-12-21
In order to get a clearer picture of your setup, how about booting your Live CD, open a Konsole, and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and what your problem might be.

---

### Post by Moonfrost on 2008-12-21
Here are the results, it seems there's no bootloader or something installed (even though I can boot into Kubuntu and see the grub menu no problem):
```

Windows is installed in the MBR of /dev/sda
No known boot loader is installed in the MBR of /dev/sdb
No known boot loader is installed in the MBR of /dev/sdc
No known boot loader is installed in the MBR of /dev/sdd
No known boot loader is installed in the MBR of /dev/sde

sda1:
    File system:  ntfs
    Boot sector  type:  Unknown
    Boot sector  info:  According to the info in the boot sector, sda1 starts at sector 63.
    Operating System: XP
    Boot files/directories present:  /boot.ini /ntldr /NTDETECT.COM

sda2:
    File system:  ext3

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1e141e13

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   168457589    84228763+   7  HPFS/NTFS
/dev/sda2   *   168457590   968141159   399841785   83  Linux
/dev/sda3       968141160   976768064     4313452+   5  Extended
/dev/sda5       968141223   976768064     4313421   82  Linux swap / Solaris


/dev/sda1: UUID="84B02CFAB02CF3F8" LABEL="Local Disk" TYPE="ntfs" 
/dev/sda2: UUID="226a5d2d-c0d9-4bfb-8ac0-60f95da5dca4" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="0816227b-a3df-4628-be28-45ba217d4f9e" 
/dev/loop0: TYPE="squashfs" 

sda1/boot.ini

[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


StdErr Messages 

Unknown MBR on /dev/sdb


Unknown MBR on /dev/sdc


Unknown MBR on /dev/sdd


Unknown MBR on /dev/sde


Unknown BootLoader  on /dev/sda1

00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  00 00 00 00 80 00 80 00  36 75 0a 0a 00 00 00 00  |........6u......|
00000030  00 00 0c 00 00 00 00 00  53 a7 a0 00 00 00 00 00  |........S.......|
00000040  f6 00 00 00 01 00 00 00  f8 f3 2c b0 fa 2c b0 84  |..........,..,..|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb b8 c0 07  |.....3.....|....|
00000060  8e d8 e8 16 00 b8 00 0d  8e c0 33 db c6 06 0e 00  |..........3.....|
00000070  10 e8 53 00 68 00 0d 68  6a 02 cb 8a 16 24 00 b4  |..S.h..hj....$..|
00000080  08 cd 13 73 05 b9 ff ff  8a f1 66 0f b6 c6 40 66  |...s......f...@f|
00000090  0f b6 d1 80 e2 3f f7 e2  86 cd c0 ed 06 41 66 0f  |.....?.......Af.|
000000a0  b7 c9 66 f7 e1 66 a3 20  00 c3 b4 41 bb aa 55 8a  |..f..f. ...A..U.|
000000b0  16 24 00 cd 13 72 0f 81  fb 55 aa 75 09 f6 c1 01  |.$...r...U.u....|
000000c0  74 04 fe 06 14 00 c3 66  60 1e 06 66 a1 10 00 66  |t......f`..f...f|
000000d0  03 06 1c 00 66 3b 06 20  00 0f 82 3a 00 1e 66 6a  |....f;. ...:..fj|
000000e0  00 66 50 06 53 66 68 10  00 01 00 80 3e 14 00 00  |.fP.Sfh.....>...|
000000f0  0f 85 0c 00 e8 b3 ff 80  3e 14 00 00 0f 84 61 00  |........>.....a.|
00000100  b4 42 8a 16 24 00 16 1f  8b f4 cd 13 66 58 5b 07  |.B..$.......fX[.|
00000110  66 58 66 58 1f eb 2d 66  33 d2 66 0f b7 0e 18 00  |fXfX..-f3.f.....|
00000120  66 f7 f1 fe c2 8a ca 66  8b d0 66 c1 ea 10 f7 36  |f......f..f....6|
00000130  1a 00 86 d6 8a 16 24 00  8a e8 c0 e4 06 0a cc b8  |......$.........|
00000140  01 02 cd 13 0f 82 19 00  8c c0 05 20 00 8e c0 66  |........... ...f|
00000150  ff 06 10 00 ff 0e 0e 00  0f 85 6f ff 07 1f 66 61  |..........o...fa|
00000160  c3 a0 f8 01 e8 09 00 a0  fb 01 e8 03 00 fb eb fe  |................|
00000170  b4 01 8b f0 ac 3c 00 74  09 b4 0e bb 07 00 cd 10  |.....<.t........|
00000180  eb f2 c3 0d 0a 41 20 64  69 73 6b 20 72 65 61 64  |.....A disk read|
00000190  20 65 72 72 6f 72 20 6f  63 63 75 72 72 65 64 00  | error occurred.|
000001a0  0d 0a 4e 54 4c 44 52 20  69 73 20 6d 69 73 73 69  |..NTLDR is missi|
000001b0  6e 67 00 0d 0a 4e 54 4c  44 52 20 69 73 20 63 6f  |ng...NTLDR is co|
000001c0  6d 70 72 65 73 73 65 64  00 0d 0a 50 72 65 73 73  |mpressed...Press|
000001d0  20 43 74 72 6c 2b 41 6c  74 2b 44 65 6c 20 74 6f  | Ctrl+Alt+Del to|
000001e0  20 72 65 73 74 61 72 74  0d 0a 00 00 00 00 00 00  | restart........|
000001f0  00 00 00 00 00 00 00 00  83 a0 b3 c9 00 00 55 aa  |..............U.|
00000200

hexdump: /dev/sdb: No medium found
hexdump: /dev/sdb: No medium found
hexdump: /dev/sdc: No medium found
hexdump: /dev/sdc: No medium found
hexdump: /dev/sdd: No medium found
hexdump: /dev/sdd: No medium found
hexdump: /dev/sde: No medium found
hexdump: /dev/sde: No medium found
/dev/sdb: No medium found

sfdisk: cannot open /dev/sdb for reading
boot_info_script.txt: line 250: 2 * : syntax error: operand expected (error token is " ")
/dev/sda: OK
```

I did this from the live disc, and I'm typing this from the live disc too as we speak.

EDIT: Here is the boot_info_script.txt results:

```
#!/bin/bash
#to use this script:
#
#sudo bash boot_info_script.txt
#
#date  12/19/08
#author  meierfra.  (with lots of input from caljohnsmith)
# 
#Looks at all MBRs and identifes the boot loader. 
#   For Grub and Supergrub:  displays the controlling partition.
#   If the  MBR's is unknown, displays the whole MBR.
#Looks at all  partitions:
#   Determines their type
#          For ntfs: displays the offset of the partition as recorded
#          in  the boot sector
#   Identifes their boot sectors.
#         For grub: displays the controlling partition and the offset
#         of the stage2 file as recorded in the boot sector.
#   Identifies the operating system
#   Lists  boot programs.
#   Displays "fdisk -lu
#   Displays "blkid -c /dev/null"
#   Displays "sfdisk -V"
#   Finds  boot directories and displays their contents.
#   For EasyBCD: finds all bootpart codes  and displays the offset
#                and boot drive its is trying to chainloade. 
#   Finds and displays  boot configuration files.
#All information is written to the file $RESULTS.txt" in the
#    same folder as the script
#
#To do:
#   Information should be displayed in a nicer format.
#   Extract info from BCD? Possible? 
#   List offsets of some boot files (for Grub error 18)
#   Boot sector info for grub is confusing.
#   Examine the  NTFS boot sector more closely to see whether
#     testdisk "RebuildBS" needs to be run.
#   Read bootpart files and copies of linus boot sector files
#       and see which boot sector it is pointing to.  
#   Test the script on different distros.
#   Use command line options, to choose what information to display.
#   On vfat partition "ntldr" and "ntdecct.com" are 
#       list in all lowercase and in all caps
#  Look into Fat boot sector, 0x80-81 bytes:   7815   6f74
#  On fedora line 230 (offset=$(hexdump -s 0x44 -n 4 -e '"%d"' $part);
#     gives a "hexdump illegal seek error" same error in one other place            


Boot_Dir="
    /Boot
    /boot
    /BOOT
    /boot/grub
    /grub
    /ubuntu/disks
    /ubuntu/disks/boot/
    /ubuntu/disks/boot/grub
    /ubuntu/disks/install/boot
    /ubuntu/disks/boot/grub
    /NST
    "

Boot_Prog="
    /bootmgr
    /BOOTMGR
    /grldr
    /GRLDR
    /ntldr
    /NTLDR
    /NTDETECT.COM
    /ntdetect.com
    /NTBOOTDD.SYS
    /ntbootdd.sys
    /wubildr.mbr
    /ubuntu/winboot/wubildr.mbr
     "

Boot_Files="
    /boot/grub/menu.lst
    /grub/menu.lst
    /menu.lst
    /ubuntu/disks/boot/grub/menu.lst
    /ubuntu/disks/install/boot/grub/menu.lst
    /boot/grub/grub.conf
    /grub/grub.conf
    /grub.conf
    /boot.ini
    /etc/fstab
    "

Dir=$(cd $(dirname $0);pwd);

LogFile=$Dir/RESULTS
while ( [ -e $LogFile$j.txt ] )
    do 
      echo j:$j 
      ((j++))
      wait;
    done
LogFile=$LogFile$j.txt



exec 6>&1   
exec >$LogFile

Folder=/tmp/BootInfo
while (! mkdir $Folder$i 2>/dev/null)
    do  
      ((i++))
      wait;
    done
Folder=$Folder$i

cd $Folder

Log1=$Folder/Log1
Error_Log=$Folder/Error_Log
Trash=$Folder/Trash
Mount_Error=$Folder/Mount_Error
Unknown_MBR=$Folder/Unknown_MBR
Tmp_Log=$Folder/Tmp_Log
exec 2>$Error_Log


Hard_Drives=$(ls /dev/hd? /dev/sd? 2>>$Trash );
for drive in $Hard_Drives;
  do 
    Message=$(echo is installed in the MBR of  $drive)
    case $(hexdump   -v -n  2 -e '/1 "%x"'  $drive) in
	eb48) BL=Grub
             dr=$(hexdump -s 0x40 -n 1 -e '"%d"' $drive);
             offset=$(hexdump -s 0x44 -n 4 -e '"%u"' $drive);
              if  [ "$offset" != 1 ];
	      then
                  pa=-1
                  for hdd in $Hard_Drives;
		  do
                      if [ $oddset -lt $(( 2 * $(sfdisk -s $hdd))) ]
			      then
		      tmp=$(dd if=$hdd skip=$offset count=1 2>>$Trash | hexdump    -n 4 -e '"%x"');
                      if [ "$tmp" = 3be5652 ]; then
                      pa=$(dd if=$hdd skip=$((offset+1)) count=1 2>>$Trash | hexdump  -s 0xa  -n 1 -e '"%d"');
                      stage2_hdd=$hdd
                      fi;
                      fi;
                  done;
                  let dr-127
                  Message=$(echo $Message and looks at sector $offset)         
                  if [ "$dr" = 128 ];
                      then
                          Message=$(echo $Message of the same hard drive) 
                      else
                           Message=$(echo $Message on boot drive \#$dr)
		  fi;
                    Message=$(echo $Message for the stage2 file.);
                    
                        if [ "$pa" = -1  ]
		     then
		         Message=$(echo $Message, but no stage2 files can be found at this location); 
                     else
                       pa=$((pa+1))
                        Message=$(echo $Message \(a  stage2 file is  at this location on $stage2_hdd\)  and on)
                        if [ $pa = 256 ];
                        then
                            Message=$(echo $Message  the same partition) 
                        else
                           Message=$(echo $Message  partition \#$pa) 
	                fi;
                       Message=$(echo $Message for menu.lst.)
                     fi;
		 
	      else
	      pa=$(hexdump -s 0x419 -n 1 -e '"%d"' $drive);
              dr=$(hexdump -s 0x41a -n 1 -e '"%d"' $drive);
              if [ $pa$dr = 4649 ]; 
		then
		BL=SuperGrub
                pa=$(hexdump -s 0x41e -n 1 -e '"%d"' $drive);
                dr=$(hexdump -s 0x41f -n 1 -e '"%d"' $drive);
 	      fi
              dr=$((dr-127))
              pa=$((pa+1))
              if [ $dr = 128 ];
               then
                Message=$(echo $Message  and  looks on the same drive in partition \#$pa  for its boot files.)
              else
               Message=$(echo $Message  and looks  on boot drive \#$dr in partition \#$pa  for its boot files.)
            fi;
	    fi;; 
 	33c0) BL=Windows;;
	fa31) BL=Syslinux;;
	faeb) BL=Lilo;; 
	fc31) BL=Testdisk;;
	eb5e) BL=Grub4Dos;;
	b800) BL=Plop;;
	33ff) BL=Gateway?;;
	fceb) BL=Bootit;;
          00) BL="No boot loader";;
	   *) BL="No known boot loader"
              echo "Unknown MBR on $drive" >> $Unknown_MBR;
              echo >> $Unknown_MBR;
              hexdump -n 512 -C $drive >> $Unknown_MBR;
              echo >> $Unknown_MBR;;
        esac;
        echo $BL $Message
  
   
 
    done
    echo


for part in $(ls /dev/hd??* /dev/sd??* 2>>$Trash)
   do
      BSI=""
      drive=${part:0:8}
      part_number=${part:8}
      part_type=$(sfdisk -c $drive $part_number)
      name=$(basename $part);
      echo  $name:;
      mkdir $name 
      type=$( /lib/udev/vol_id -t $part 2>$Tmp_Log );
      if [ $part_type = 5 ] || [ $part_type = f ] && [ "$type" = "" ] ;
         then
	 type="Extended Partition";
	 cat $Tmp_Log>>$Trash;
	 else
         cat $Tmp_Log>>$Error_Log
      fi;
      echo "    File system:  "$type;
      if [ "$type" != "swap" ]  && [ "$type" != "Extended Partition"  ] && [ "$type" != "unknown volume type" ] && [ "$type" != "LVM2_member" ]  ;
       then 
      if  mount $part $name 2>$Mount_Error; then
      if [ "$type" = "ntfs" ];
         then
         offset=$(hexdump -s 0x1c -n 4 -e '"%d\n"' $part);
         BSI=$(echo  According to  the  info in the boot sector, $name starts at sector $offset.)   
      fi;
          case $(hexdump -v -s 0x80 -n  2 -e '/1 "%x"'  $part) in
            08cd) BST=XP;;
            b6d1) BST=XP;;
	    55aa) BST=Vista;;           
	    5272) BST=Grub;
                  offset=$(hexdump -s 0x44 -n 4 -e '"%u"' $part);
                  dr=$(hexdump -s 0x40 -n 1 -e '"%d"' $part);
                   pa=-1
                  for hdd in $Hard_Drives;
		  do
                      if [ $offset -lt  $(( 2 * $(sfdisk -s $hdd))) ];
			      then
		      tmp=$(dd if=$hdd skip=$offset count=1 2>>$Trash | hexdump    -n 4 -e '"%x"');
                      if [ "$tmp" = 3be5652 ]; then
                      pa=$(dd if=$hdd skip=$((offset+1)) count=1 2>>$Trash | hexdump  -s 0xa  -n 1 -e '"%d"');
                      stage2_hdd=$hdd
                      fi;
		      fi;
                  done;
                  dr=$((dr-127))
                  BSI=$(echo $BSI Grub is installed to the boot sector of $part and looks at sector $offset )        
                  if [ "$dr" = 128 ];
                      then
                          BSI=$(echo $BSI of the same hard drive) 
                      else
                          BSI=$(echo $BSI on boot drive \#$dr)
		  fi;
                  BSI=$(echo $BSI for the stage2 file.);
                    
                        if [ "$pa" = T  ]
		     then
		        BSI=$(echo $BSI, but no stage2 files can be found at this location); 
                     else
                       pa=$((pa+1))
                       BSI=$(echo $BSI  \(a  stage2 file is  at this location on $stage2_hdd\)  and on )                       
                        if [ "$pa" = 256 ];
                        then
                           BSI=$(echo $BSI the same partition) 
                        else
                            BSI=$(echo $BSI  partition \#$pa )
	                fi;
                      BSI=$(echo $BSI for menu.lst.)
                     fi;;
                  
                   
            7cc6) BST=Win_98;;
            7304) BST=Dos_1.0;;
            2d5e) BST=Dos_1.1;;
	    7815) BST=Fat;;
            6f74) BST=Fat;;
 	      00) sig2=$(hexdump -v -s 0x80 -n  2 -e '/1 "%x"'  $part)
                      if [ "$sig2" = 00 ];
		      then
                      BST="No Boot Loader";
		      else
		      BST="Unknown"
                      echo "Unknown BootLoader  on $part" >> $Unknown_MBR;
                      echo >> $Unknown_MBR;
                      hexdump -n 512 -C $part >> $Unknown_MBR;
                      echo >> $Unknown_MBR;
                  fi;;
                *) BST="Unknown"
                   echo "Unknown BootLoader  on $part" >> $Unknown_MBR;
                   echo >> $Unknown_MBR;
                   hexdump -n 512 -C $part >> $Unknown_MBR;
                   echo >> $Unknown_MBR;
            esac;

       OS=""
       [ -e $name"/Windows/System32/config/BCD-Template" ] ||  [ -e $name"/windows/system32/config/bcd-template" ] || [ -e $name"/WINDOWS/System32/config/BCD-Template" ] ||
  [ -e $name"/WINDOWS/system32/config/BCD-Template" ] && OS=Vista

       [ -e $name"/Windows/System32/config/SecEvent.Evt" ] ||  [ -e $name"/WINDOWS/system32/config/SecEvent.Evt" ] || [ -e $name"/WINDOWS/system32/config/secevent.evt" ] || [ -e $name"/windows/system32/config/secevent.evt" ] && OS=XP
  
       [ -e $name"/etc" ] && OS=$(cat $name/etc/issue)
     

       BootFiles=""
       for file in $Boot_Files;
       do
           if [ -e $name$file ];
              then BootFiles=$(echo $BootFiles"  "$file);
	      echo >> $Log1
	      echo $name$file >> $Log1;
              echo >> $Log1
              cat $name$file >> $Log1;
	   fi;
       done;

       for file in $Boot_Prog;
       do
           if [ -e $name$file ];
              then BootFiles=$(echo $BootFiles"  "$file);          
	   fi;
       done;

       for file in $Boot_Dir;
       do
           if [ -e $name$file ];
              then BootFiles=$(echo $BootFiles"  "$file); 
	      echo >> $Log1
	      echo $name$file >> $Log1;
              echo >> $Log1
              ls -la  $name$file >> $Log1 ; 
              if [ "$file" = "/NST" ];
		  then
		  for loader in $( ls  $name$file );
		  do
                      sig=$(hexdump -s 0x101 -n 8  -e '8/1 "%_p"' $name$file/$loader)
                      if [ "$sig"  = "BootPart" ]
			  then
                          offset=$(hexdump -s 0xf1 -n 4 -e '"%d"' $name$file/$loader);
                              dr=$(hexdump -s 0x6f -n 1 -e '"%d"' $name$file/$loader);
			      dr=$((dr -127))
 			  BSI=$(echo $BSI "  "BootPart in $loader is trying to chain load sector \#$offset on boot drive \#$dr);
		       fi;
		  done;
               fi;
	   fi;
       done;

      echo "    Boot sector  type:  "$BST
      echo "    Boot sector  info:  "$BSI  
      echo "    Operating System: "$OS
      echo "    Boot files/directories present: " $BootFiles
     
     umount $name ;
     else
     echo "    Mounting failed:  ";  
     cat   $Mount_Error;
     fi;
     fi;
     echo;
 
     done;

fdisk -lu;
echo;
sfdisk -V
echo;
blkid -c /dev/null
echo >> $Log1
echo "StdErr Messages ">>$Log1
echo >> $Log1
cat $Log1
[ -e $Unknown_MBR ] && cat $Unknown_MBR
cat $Error_Log
chown $(basename ~) $LogFile
exec 1>&-
exec 1>&6
exec 6>&-
echo Finished. The results are in the file $(basename $LogFile)   located in $Dir
```

---

### Post by caljohnsmith on 2008-12-21
It looks like the solution to your problem might be really simple. How about changing your Kubuntu menu.lst to use the following entry for Windows:
```
title          Windows XP
root           (hd0,0)
chainloader +1
```
Also, you are currently using the Windows MBR to boot Grub in the boot sector of your Kubuntu partition. That's OK, but if you want avoid trouble, just make sure not to use the "makeactive" line then in your menu.lst entries, because "makeactive" sets the boot flag on a partition. Also, you wouldn't want to change the boot flag from the Kubuntu partition to any other partition if you want Grub on start up. But anyway, go ahead and reboot, and please let me know exactly what happens when you boot Windows from Grub.

---

### Post by Moonfrost on 2008-12-21
> **caljohnsmith said:**
> It looks like the solution to your problem might be really simple. How about changing your Kubuntu menu.lst to use the following entry for Windows:
```
title          Windows XP
root           (hd0,0)
chainloader +1
```
Also, you are currently using the Windows MBR to boot Grub in the boot sector of your Kubuntu partition. That's OK, but if you want avoid trouble, just make sure not to use the "makeactive" line then in your menu.lst entries, because "makeactive" sets the boot flag on a partition. Also, you wouldn't want to change the boot flag from the Kubuntu partition to any other partition if you want Grub on start up. But anyway, go ahead and reboot, and please let me know exactly what happens when you boot Windows from Grub.

I'm not sure what I've done wrong, I never even had problems dual-booting before following the exact same procedures in the exact same order...who knows, anyway I'll get back to you in a sec...

EDIT: That worked!!! thanks a bunch!!...BUT! you said I'm using the Windows MBR to boot right? is there any way I can change to the Linux/Kubuntu MBR? because I don't want to have problems since Kubuntu is my main OS while Windows is in a small partition for a few things like Windows Live Messenger and maybe 2 or 3 more things but that's it.

I only did this whole thing "again" because I just replaced a hard drive 2 weeks ago, the original 200gb hard drive that came with my OEM PC after 2 years of abuse finally gave up one day while browsing the web, it started doing the famous clicking noises and then my OS froze, I could never boot the PC again. I bought a 500gb drive and I wanted to make a slightly bigger partition for Windows but it turns out it takes forever to do that now because of the hard drive being so big.

---

### Post by meierfra. on 2008-12-21
Hi Moonfrost,

I'm the author of the script "boot_info_script.txt". There seems to be a small bug in the script. I did some changes, but I'm not sure that it cured the problem. Could you follow the instruction from post #4 one more time?

Could you also post the output of

```
ls -l /dev/sd*
```

Thanks.

---

### Post by meierfra. on 2008-12-21
> is there any way I can change to the Linux/Kubuntu MBR?  


Yes, just  do

```
sudo grub
```

and at the grub prompt,

```
root (hd0,1)
setup (hd0)
quit
```

---

### Post by caljohnsmith on 2008-12-21
[QUOTE=Moonfrost]EDIT: That worked!!! thanks a bunch!!...BUT! you said I'm using the Windows MBR to boot right? is there any way I can change to the Linux/Kubuntu MBR? because I don't want to have problems since Kubuntu is my main OS while Windows is in a small partition for a few things like Windows Live Messenger and maybe 2 or 3 more things but that's it.[/QUOTE]
You're welcome, I'm glad that did the trick. To install Grub to the MBR, just follow meierfra's post. Also, if it's not too much to ask, please help out meierfra by running the script again, because it would help him debug the script and make it more usable for everyone. :)

---

### Post by Moonfrost on 2008-12-22
> **meierfra. said:**
> Hi Moonfrost,

I'm the author of the script "boot_info_script.txt". There seems to be a small bug in the script. I did some changes, but I'm not sure that it cured the problem. Could you follow the instruction from post #4 one more time?

Could you also post the output of

```
ls -l /dev/sd*
```

Thanks.

Here you go:

boot_info_script.txt:

```
!/bin/bash
#to use this script:
#
#sudo bash boot_info_script.txt
#
#date  12/21/08
#author  meierfra.  (with lots of input from caljohnsmith)
# 
#Looks at all MBRs and identifes the boot loader. 
#   For Grub and Supergrub:  displays the controlling partition.
#   If the  MBR's is unknown, displays the whole MBR.
#Looks at all  partitions:
#   Determines their type
#          For ntfs: displays the offset of the partition as recorded
#          in  the boot sector
#   Identifes their boot sectors.
#         For grub: displays the controlling partition and the offset
#         of the stage2 file as recorded in the boot sector.
#   Identifies the operating system
#   Lists  boot programs.
#   Displays "fdisk -lu
#   Displays "blkid -c /dev/null"
#   Displays "sfdisk -V"
#   Finds  boot directories and displays their contents.
#   For EasyBCD: finds all bootpart codes  and displays the offset
#                and boot drive its is trying to chainloade. 
#   Finds and displays  boot configuration files.
#All information is written to the file $RESULTS.txt" in the
#    same folder as the script
#
#To do:
#   Information should be displayed in a nicer format.
#   Extract info from BCD? Possible? 
#   List offsets of some boot files (for Grub error 18)
#   Boot sector info for grub is confusing.
#   Examine the  NTFS boot sector more closely to see whether
#     testdisk "RebuildBS" needs to be run.
#   Read bootpart files and copies of linus boot sector files
#       and see which boot sector it is pointing to.  
#   Test the script on different distros.
#   Use command line options, to choose what information to display.
#   On vfat partition "ntldr" and "ntdecct.com" are 
#       list in all lowercase and in all caps
#  Look into Fat boot sector, 0x80-81 bytes:   7815   6f74


Boot_Dir="
    /Boot
    /boot
    /BOOT
    /boot/grub
    /grub
    /ubuntu/disks
    /ubuntu/disks/boot/
    /ubuntu/disks/boot/grub
    /ubuntu/disks/install/boot
    /ubuntu/disks/boot/grub
    /NST
    "

Boot_Prog="
    /bootmgr
    /BOOTMGR
    /grldr
    /GRLDR
    /ntldr
    /NTLDR
    /NTDETECT.COM
    /ntdetect.com
    /NTBOOTDD.SYS
    /ntbootdd.sys
    /wubildr.mbr
    /ubuntu/winboot/wubildr.mbr
     "

Boot_Files="
    /boot/grub/menu.lst
    /grub/menu.lst
    /menu.lst
    /ubuntu/disks/boot/grub/menu.lst
    /ubuntu/disks/install/boot/grub/menu.lst
    /boot/grub/grub.conf
    /grub/grub.conf
    /grub.conf
    /boot.ini
    /etc/fstab
    "

Dir=$(cd $(dirname $0);pwd);

LogFile=$Dir/RESULTS
while ( [ -e $LogFile$j.txt ] )
    do  
      ((j++))
      wait;
    done
LogFile=$LogFile$j.txt



exec 6>&1   
exec >$LogFile

Folder=/tmp/BootInfo
while (! mkdir $Folder$i 2>/dev/null)
    do  
      ((i++))
      wait;
    done
Folder=$Folder$i

cd $Folder

Log1=$Folder/Log1
Error_Log=$Folder/Error_Log
Trash=$Folder/Trash
Mount_Error=$Folder/Mount_Error
Unknown_MBR=$Folder/Unknown_MBR
Tmp_Log=$Folder/Tmp_Log
exec 2>$Error_Log


Hard_Drives=$(ls /dev/hd? /dev/sd? 2>>$Trash );
for drive in $Hard_Drives;
  do 
    Message=$(echo is installed in the MBR of  $drive)
    case $(hexdump   -v -n  2 -e '/1 "%x"'  $drive) in
	eb48) BL=Grub
             dr=$(hexdump -s 0x40 -n 1 -e '"%d"' $drive);
             offset=$(hexdump -s 0x44 -n 4 -e '"%u"' $drive);
              if  [ "$offset" != 1 ];
	      then
                  pa=-1
                  for hdd in $Hard_Drives;
		  do
                      if [ $oddset -lt $((2*$(sfdisk -s $hdd))) ]
			      then
		      tmp=$(dd if=$hdd skip=$offset count=1 2>>$Trash | hexdump    -n 4 -e '"%x"');
                      if [ "$tmp" = 3be5652 ]; then
                      pa=$(dd if=$hdd skip=$((offset+1)) count=1 2>>$Trash | hexdump  -s 0xa  -n 1 -e '"%d"');
                      stage2_hdd=$hdd
                      fi;
                      fi;
                  done;
                  let dr-127
                  Message=$(echo $Message and looks at sector $offset)         
                  if [ "$dr" = 128 ];
                      then
                          Message=$(echo $Message of the same hard drive) 
                      else
                           Message=$(echo $Message on boot drive \#$dr)
		  fi;
                    Message=$(echo $Message for the stage2 file.);
                    
                        if [ "$pa" = -1  ]
		     then
		         Message=$(echo $Message, but no stage2 files can be found at this location); 
                     else
                       pa=$((pa+1))
                        Message=$(echo $Message \(a  stage2 file is  at this location on $stage2_hdd\)  and on)
                        if [ $pa = 256 ];
                        then
                            Message=$(echo $Message  the same partition) 
                        else
                           Message=$(echo $Message  partition \#$pa) 
	                fi;
                       Message=$(echo $Message for menu.lst.)
                     fi;
		 
	      else
	      pa=$(hexdump -s 0x419 -n 1 -e '"%d"' $drive);
              dr=$(hexdump -s 0x41a -n 1 -e '"%d"' $drive);
              if [ $pa$dr = 4649 ]; 
		then
		BL=SuperGrub
                pa=$(hexdump -s 0x41e -n 1 -e '"%d"' $drive);
                dr=$(hexdump -s 0x41f -n 1 -e '"%d"' $drive);
 	      fi
              dr=$((dr-127))
              pa=$((pa+1))
              if [ $dr = 128 ];
               then
                Message=$(echo $Message  and  looks on the same drive in partition \#$pa  for its boot files.)
              else
               Message=$(echo $Message  and looks  on boot drive \#$dr in partition \#$pa  for its boot files.)
            fi;
	    fi;; 
 	33c0) BL=Windows;;
	fa31) BL=Syslinux;;
	faeb) BL=Lilo;; 
	fc31) BL=Testdisk;;
	eb5e) BL=Grub4Dos;;
	b800) BL=Plop;;
	33ff) BL=Gateway?;;
	fceb) BL=Bootit;;
          00) BL="No boot loader";;
	   *) BL="No known boot loader"
              echo "Unknown MBR on $drive" >> $Unknown_MBR;
              echo >> $Unknown_MBR;
              hexdump -n 512 -C $drive >> $Unknown_MBR;
              echo >> $Unknown_MBR;;
        esac;
        echo $BL $Message
  
   
 
    done
    echo


for part in $(ls /dev/hd??* /dev/sd??* 2>>$Trash)
   do
      BSI=""
      drive=${part:0:8}
      part_number=${part:8}
      part_type=$(sfdisk -c $drive $part_number)
      name=$(basename $part);
      echo  $name:;
      mkdir $name 
      type=$( /lib/udev/vol_id -t $part 2>$Tmp_Log );
      if [ $part_type = 5 ] || [ $part_type = f ] && [ "$type" = "" ] ;
         then
	 type="Extended Partition";
	 cat $Tmp_Log>>$Trash;
	 else
         cat $Tmp_Log>>$Error_Log
      fi;
      echo "    File system:  "$type;
      if [ "$type" != "swap" ]  && [ "$type" != "Extended Partition"  ] && [ "$type" != "unknown volume type" ] && [ "$type" != "LVM2_member" ]  ;
       then 
      if  mount $part $name 2>$Mount_Error; then
      if [ "$type" = "ntfs" ];
         then
         offset=$(hexdump -s 0x1c -n 4 -e '"%d\n"' $part);
         BSI=$(echo  According to  the  info in the boot sector, $name starts at sector $offset.)   
      fi;
          case $(hexdump -v -s 0x80 -n  2 -e '/1 "%x"'  $part) in
             8cd) BST=XP;;
            b6d1) BST=XP;;
	    55aa) BST=Vista;;           
	    5272) BST=Grub;
                  offset=$(hexdump -s 0x44 -n 4 -e '4 "%u"' $part 2>>$Trash);
                  dr=$(hexdump -s 0x40 -n 1 -e '"%d"' $part);
                  pa=-1
                  for hdd in $Hard_Drives;
		  do
                      if [ $offset -lt  $((2*$(sfdisk -s $hdd))) ];
			      then
		      tmp=$(dd if=$hdd skip=$offset count=1 2>>$Trash | hexdump    -n 4 -e '"%x"');
                      if [ "$tmp" = 3be5652 ]; then
                      pa=$(dd if=$hdd skip=$((offset+1)) count=1 2>>$Trash | hexdump  -s 0xa  -n 1 -e '"%d"');
                      stage2_hdd=$hdd
                      fi;
		      fi;
                  done;
                  dr=$((dr-127))
                  BSI=$(echo $BSI Grub is installed to the boot sector of $part and looks at sector $offset )        
                  if [ "$dr" = 128 ];
                      then
                          BSI=$(echo $BSI of the same hard drive) 
                      else
                          BSI=$(echo $BSI on boot drive \#$dr)
		  fi;
                  BSI=$(echo $BSI for the stage2 file.);
                    
                        if [ "$pa" = T  ]
		     then
		        BSI=$(echo $BSI, but no stage2 files can be found at this location); 
                     else
                       pa=$((pa+1))
                       BSI=$(echo $BSI  \(a  stage2 file is  at this location on $stage2_hdd\)  and on )                       
                        if [ "$pa" = 256 ];
                        then
                           BSI=$(echo $BSI the same partition) 
                        else
                            BSI=$(echo $BSI  partition \#$pa )
	                fi;
                      BSI=$(echo $BSI for menu.lst.)
                     fi;;
                  
                   
            7cc6) BST=Win_98;;
            7304) BST=Dos_1.0;;
            2d5e) BST=Dos_1.1;;
	    7815) BST=Fat;;
            6f74) BST=Fat;;
 	      00) sig2=$(hexdump -v -s 0x80 -n  2 -e '/1 "%x"'  $part)
                      if [ "$sig2" = 00 ];
		      then
                      BST="No Boot Loader";
		      else
		      BST="Unknown"
                      echo "Unknown BootLoader  on $part" >> $Unknown_MBR;
                      echo >> $Unknown_MBR;
                      hexdump -n 512 -C $part >> $Unknown_MBR;
                      echo >> $Unknown_MBR;
                  fi;;
                *) BST="Unknown"
                   echo "Unknown BootLoader  on $part" >> $Unknown_MBR;
                   echo >> $Unknown_MBR;
                   hexdump -n 512 -C $part >> $Unknown_MBR;
                   echo >> $Unknown_MBR;
            esac;

       OS=""
       [ -e $name"/Windows/System32/config/BCD-Template" ] ||  [ -e $name"/windows/system32/config/bcd-template" ] || [ -e $name"/WINDOWS/System32/config/BCD-Template" ] ||
  [ -e $name"/WINDOWS/system32/config/BCD-Template" ] && OS=Vista

       [ -e $name"/Windows/System32/config/SecEvent.Evt" ] ||  [ -e $name"/WINDOWS/system32/config/SecEvent.Evt" ] || [ -e $name"/WINDOWS/system32/config/secevent.evt" ] || [ -e $name"/windows/system32/config/secevent.evt" ] && OS=XP
  
       [ -e $name"/etc" ] && OS=$(cat $name/etc/issue)
     

       BootFiles=""
       for file in $Boot_Files;
       do
           if [ -e $name$file ];
              then BootFiles=$(echo $BootFiles"  "$file);
	      echo >> $Log1
	      echo $name$file >> $Log1;
              echo >> $Log1
              cat $name$file >> $Log1;
	   fi;
       done;

       for file in $Boot_Prog;
       do
           if [ -e $name$file ];
              then BootFiles=$(echo $BootFiles"  "$file);          
	   fi;
       done;

       for file in $Boot_Dir;
       do
           if [ -e $name$file ];
              then BootFiles=$(echo $BootFiles"  "$file); 
	      echo >> $Log1
	      echo $name$file >> $Log1;
              echo >> $Log1
              ls -la  $name$file >> $Log1 ; 
              if [ "$file" = "/NST" ];
		  then
		  for loader in $( ls  $name$file );
		  do
                      sig=$(hexdump -s 0x101 -n 8  -e '8/1 "%_p"' $name$file/$loader)
                      if [ "$sig"  = "BootPart" ]
			  then
                          offset=$(hexdump -s 0xf1 -n 4 -e '"%d"' $name$file/$loader);
                              dr=$(hexdump -s 0x6f -n 1 -e '"%d"' $name$file/$loader);
			      dr=$((dr -127))
 			  BSI=$(echo $BSI "  "BootPart in $loader is trying to chain load sector \#$offset on boot drive \#$dr);
		       fi;
		  done;
               fi;
	   fi;
       done;

      echo "    Boot sector  type:  "$BST
      echo "    Boot sector  info:  "$BSI  
      echo "    Operating System: "$OS
      echo "    Boot files/directories present: " $BootFiles
     
     umount $name ;
     else
     echo "    Mounting failed:  ";  
     cat   $Mount_Error;
     fi;
     fi;
     echo;
 
     done;

for drive in $Hard_Drives;
 do
     fdisk -lu $drive;
     echo;
     sfdisk -V $drive 2>>$Tmp_Log;
     cat  $Tmp_Log;
     echo;
 done
blkid -c /dev/null
echo >> $Log1
echo "StdErr Messages ">>$Log1
echo >> $Log1
cat $Log1
[ -e $Unknown_MBR ] && cat $Unknown_MBR
cat $Error_Log
chown $(basename ~) $LogFile
exec 1>&-
exec 1>&6
exec 6>&-
echo Finished. The results are in the file $(basename $LogFile)   located in $Dir
```

Here's the output of -l /dev/sd*

```
ubuntu@ubuntu:~/Desktop$ ls -l /dev/sd*
brw-rw---- 1 root disk 8,  0 2008-12-22 16:30 /dev/sda
brw-rw---- 1 root disk 8,  1 2008-12-22 16:26 /dev/sda1
brw-rw---- 1 root disk 8,  2 2008-12-22 16:30 /dev/sda2
brw-rw---- 1 root disk 8,  3 2008-12-22 16:26 /dev/sda3
brw-rw---- 1 root disk 8,  5 2008-12-22 16:26 /dev/sda5
brw-rw---- 1 root disk 8, 16 2008-12-22 16:26 /dev/sdb
brw-rw---- 1 root disk 8, 32 2008-12-22 16:26 /dev/sdc
brw-rw---- 1 root disk 8, 48 2008-12-22 16:26 /dev/sdd
brw-rw---- 1 root disk 8, 64 2008-12-22 16:26 /dev/sde
```

Note that I did this from the live disc, if you need me to do it again from the OS just ask, by the way thanks for your script, it helped to understand a few more things about this.

---

### Post by meierfra. on 2008-12-22
Thanks for the information. Could you also post the content of "RESULTS.tex"?  (Since you run the script from the Live CD you will have to repeat the instructions for post 4 again).

Thanks

---

### Post by meierfra. on 2008-12-22
Ignore my previous post. There is another case in the forums  where the script is still malfunctioning at a similar place. I'll try to find a fix and might ask you to tun the script again sometime later.

---

### Post by meierfra. on 2008-12-22
I'm pretty sure the bug is fixed now. So  could  you follow the instruction from  post 4  again?   If you still have "RESULT.txt" on your desktop from the last time, delete it first. (You don't need to post "boot_info_script.txt", only the new "RESULT.txt")

---

