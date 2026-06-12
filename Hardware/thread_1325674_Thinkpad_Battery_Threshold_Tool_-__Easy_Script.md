---
title: "Thinkpad Battery Threshold Tool -  Easy Script"
date: 2009-11-13
forum: Hardware
---

### Post by hellmet on 2009-11-13
I have written a Python script that (hopefully) eases control over Thinkpad battery thresholds - using tp-smapi and sysfs. I have a Thinkpad R500 and the script works well on my machine. I have NOT tested it on any other Thinkpad, and I would really appreciate feedback (and bug reports) from you.

I have never written Python scripts for public before, and who knows, this script might not even work on your machine. Just let me know.

**What it does: **
Check for, and install tp_smapi, sysfs.
Displays which battery(ies) are installed and their cycle counts.
Lets you manage thresholds for integrated battery.
Saves settings on reboot.

**Working on:**
-Support for second or Ultrabay battery- I'm working on it. I'm new to Python, and I don't have an ultrabay, so will take some time.
-A GUI for this tool. (If this script does work, that is)

A screenshot of the script on a terminal:
[IMG]http://img526.imageshack.us/img526/9215/screenshot1ig.png[/IMG]

[B]How to run the script:

[/B]-Download the attachment - **TPTool-&#9788;J-v0.04.py** from this post. - I recommend you right click -> Save As, to your home directory - so you don't need to figure out where the file downloaded.
-Open a terminal, CD to the directory where you downloaded the file.
-And type (or copy/paste this):
```
sudo python TPTool-&#9788;J-v0.04.py
```Let me know how it goes.

P.S.: This script can be run everytime you want to change thresholds. tp-smapi and sysfs packages are checked for installation each time, but only installed if using the script the first time.

---

### Post by Ynot_Not on 2009-11-23
I followed the instructions on at TP600X that is running Mint8 RC. I was able to view, set, change the start/end charging %'s without issue. I had no issues installing Mint, yet I'm unable to install tpctl as I'd like more control over battery use/charging. Any thoughts?

TM

---

### Post by hellmet on 2009-11-23
I really did not understand your post. You say you were able to follow instructions (of this thread?) and set and change thresholds. Your second part of the post mentions not being able to install tpctl.

Well, if I'm not wrong, tpctl was supposed to be used on older Thinkpads. To control thresholds on newer Thinkpads, the tp_smapi module is used to control thresholds. And, I think 600X is an older Thinkpad. My script only works for newer Thinkpads (using tp_smapi).

Also, what do you mean by "more control". Do you need the script to incorporate more features? 

Regards

---

### Post by Super_moose on 2009-11-27
Quick question, what is CDing to the directory? I'm not very familure with using the terminal besides just copy and pasting what people tell me to do.

---

### Post by hellmet on 2009-11-27
```
cd /home/user
```
CD stands for Change Directory. Replace 'user' in the above code with your username.

---

### Post by firsttimeuser on 2009-12-01
hats off to you sir!

---

### Post by emeraldgirl08 on 2009-12-15
Am going now for a reboot.

I downloaded and ran the Python script.

If this works I'll be back with a report!

I set my thresholds for 85% (start charge)
                        90% (stop charge)

:D

[B]EDIT:
[/B]
I rebooted and ran the python again. The percentages I set are still there!

I posted something about finding a program of this type and here it is :)

FYI I am a Thinkpad girl so I really appreciate you taking the time to compile this. TY.

Forgot to add I am running Karmic on an R51e. I wonder if this will work with Crunchbang? It is based on Jaunty so I'm thinking it may. That's good news for my R52 if it works :)

**Update: **

This works on Crunchbang 9.04 also :)

---

### Post by hellmet on 2009-12-16
Glad that the script has been of some use to you. Let me find some time and I will write a GUI for this. 
Btw, anybody here use an Ultrabay? Just wondering if I should add support for that second battery or if I should skip it for now.

---

### Post by psrivats on 2010-01-10
Works on a T60p with Karmic. Thank you!

---

### Post by emeraldgirl08 on 2010-02-07
Hi Helmett *wave*

I recently installed Karmic on my T400 and running the python script comes back with a Fatal: module tp_smapi not found. I don't know how I should proceed with this. FYI I'm running 64-bit Karmic and am on kernel 2.6.31.19. If you have any suggestions I would really appreciate it. TIA.

---

### Post by moixa on 2010-02-07
> **emeraldgirl08 said:**
> Hi Helmett *wave*

I recently installed Karmic on my T400 and running the python script comes back with a Fatal: module tp_smapi not found. I don't know how I should proceed with this. FYI I'm running 64-bit Karmic and am on kernel 2.6.31.19. If you have any suggestions I would really appreciate it. TIA.

tp_smapi is not longer included as a binary module, though you can still compile it using module-assistant

Install module-assistant, run it, select tp-smapi, then select Build, done!

---

### Post by moixa on 2010-02-07
I have a problem on sysfsutils.
It doesn't start automatically even after I did service sysfsutils defaults
as a result, my threshold settings in /etc/sysfs.conf aren't read during start up.
Anyone knows how to solve it?

---

### Post by Chemtox on 2010-02-13
The script did the trick flawlessly, thanks!

But then the thresholds went back to 96-100 mysteriously.  TPTool would still show the ones I set, but while listing the available batteries it would also produce "grep: /sys/devices/platform/smapi/BAT0/installed: No such file or directory."  The smapi module was not loading anymore.

The culprit was, of course, the dreaded kernel upgrade.  Rebuilding the module with "m-a a-i tp-smapi-source; modprobe tp_smapi" made it all good again.

Isn't there a mechanism to automatically recompile stuff with a kernel upgrade?

---

### Post by hellmet on 2010-02-24
I have not worked on the script to automatically check for and upgrade during a kernel upgrade. My script is very basic and hardly has any advanced code. I will look at the code sometime and see if I can do something about this issue. Sorry for the trouble.

---

### Post by Chemtox on 2010-02-24
> **hellmet said:**
> I have not worked on the script to automatically check for and upgrade during a kernel upgrade. My script is very basic and hardly has any advanced code. I will look at the code sometime and see if I can do something about this issue. Sorry for the trouble.

Not at all, I know your script is simple, and it's fine that way.  I just mentioned my problem here because most probably someone else will find it too.

I was wondering if *Ubuntu* has a (also simple) mechanism to recompile stuff on kernel upgrade, since I'm sure there are many 3rd party programs/modules that require so.  Probably a debconf trigger, but I'm not familiar with it.

Cheers!

---

### Post by JohnsonCT on 2010-05-13
I don't know if I'm missing something, but this python script comes up garbled on my side and python gives me the following error when trying to run it:

> SyntaxError: Non-UTF-8 code starting with '\xd1' in file TPTool-&#9788;J-v0.04.py on line 1, but no encoding declared; see [http://python.org/dev/peps/pep-0263/](http://python.org/dev/peps/pep-0263/) for details


I've downloaded it multiple times on multiple machines and I get the same result every time. The md5 sum I get on the file is 0cd739965f7164040656371016301684. Would anyone care to help me with this?

---

### Post by sicvolo on 2010-05-25
Confirmed, works on T61 on Lucid.

Next time, please, provide the scripts in the source code format if you expect people to run them with sudo privileges. And name files properly - without unicode symbols and with proper extensions (pyc, not py if it is compiled python)

Decompiling python is trivial, but you could have saved the hassle for those who do not trust root credentials to code they can not see.

---

### Post by sicvolo on 2010-05-25
> **Chemtox said:**
> I was wondering if *Ubuntu* has a (also simple) mechanism to recompile stuff on kernel upgrade, since I'm sure there are many 3rd party programs/modules that require so. 

Yes, try this - sudo aptitude install tp-smapi-dkms

instead of the tp-smapi-source+m-a that the script does.

---

### Post by hellmet on 2010-05-30
> **sicvolo said:**
> Confirmed, works on T61 on Lucid.

Next time, please, provide the scripts in the source code format if you expect people to run them with sudo privileges. And name files properly - without unicode symbols and with proper extensions (pyc, not py if it is compiled python)

Decompiling python is trivial, but you could have saved the hassle for those who do not trust root credentials to code they can not see.
Point taken.

> **sicvolo said:**
> Yes, try this - sudo aptitude install tp-smapi-dkms

instead of the tp-smapi-source+m-a that the script does.
Great, thanks! Will try that when I can.

---

### Post by kkfok1 on 2010-06-29
Thanks. It works on T61 Lucid.

---

### Post by dgokhale on 2010-08-22
Hi.. I have an ideapad u460. i tried installing tp-smapi-dkms and got a fatal error at the modprobe stage.

Seems this does not work on an ideapad. Any pointer to what does?

Regards and thanks

D

---

### Post by lunatico on 2010-09-10
Hi!

The script seems to be working fine... I had changed my thresholds manually already, what I'm looking for is how to change the threshold values in the BIOS also. Because at the moment if I turn off the laptop and leave it plugged or in the docking station it gets charged to 100% again.
I'm almost sure there is a way to do this, I think in Windows when using Lenovo's software it also changes the values in the BIOS, but not sure because I never used Windows at all in this thinkpad.

Any ideas anyone?

Also: could you provide the source code as mentioned before?

Thanks!

---

### Post by era86 on 2010-11-04
Sorry if this is considered necromancing, but I was wondering if this script is still up to date since September.  I guess I could try using it, but I want to minimize the chance of messing up my kernel build as much as possible.

Any input would be greatly appreciated.  Thank you!
:guitar:

---

### Post by Chemtox on 2010-11-04
Yes, it does still works, nothing has broken in a whole month.  And nothing will break for a few more months, if not years, most probably.  Contrary to what some would like you to believe, Linux is not as wild nor prone to change. ;)

Also, you shouldn't need to touch your kernel, unless you have got a bizarre custom build.  With a normal Ubuntu install, you only need sysfsutils and the tp-smapi module, both available at your favorite repository, and the script will check for them and install them if they are needed, so all you have to do is run it!

The script, however, only builds the smapi module for your current kernel, and you will have to rebuild it with every new kernel.  But if you install tp-smapi-dkms (as suggested by [sicvolo]("http://ubuntuforums.org/member.php?u=813448")) before running the script, the Dynamic Kernel Module Support will take care of that for you.

It would be nice if the script installed the dkms package by itself though, and perhaps if it read the current thresholds from the actual /sys files instead of sysfs.conf, so it doens't gives the impression of being working when it's not, like when /sys/devices/platform/smapi/ is not actually there.  :P *pokes Hellmet*

---

### Post by optimisteo on 2011-01-11
Hi!
Could you please provide the source code?
As it has been pointed out no one should sudo unknown code.
Although someone suggested decompiling was trivial, i am not familiar with the technique and considering this is a free software forum sharing the source would save the "reverse engineering" and be indeed much appreciated.

Thanks,

Opti

---

### Post by hellmet on 2011-01-11
Guys sorry about the source code. The thinkpad that I used died quite sometime back and I won't be able to paste the code here. Please delete this thread if you find it against the forum rules.

---

### Post by alickw on 2011-01-18
I've disassembled the Python script TPTool-&#9788;J-v0.04.py using UnPyc ([http://sourceforge.net/projects/unpyc/](http://sourceforge.net/projects/unpyc/)). Refer below.

Alick Wilson

---------------------------------------

--== Disasm ==--
00000008 CODE:
             argcount:
00000009         LONG: 0L (00 00 00 00)
             nlocals:
0000000D         LONG: 0L (00 00 00 00)
             stacksize:
00000011         LONG: 10L (0A 00 00 00)
             flags:
00000015         LONG: 64L (40 00 00 00)
                 (NOFREE)
             code:
00000019         STR: 'd\x00\x00d\x01\x00k\x00\x00Z\x00\x00d\x00\x00d\x01\x00k\x01\x00Z\x01\x00d\x02\x00GHd\x03\x00GHd...' (F7 03 00 00 64 00 00 64 01 00 6B 00...)
                 00000000     64 - LOAD_CONST          -1
                 00000003     64 - LOAD_CONST          None
                 00000006     6B - IMPORT_NAME         'os'
                 00000009     5A - STORE_NAME          'os'
                 0000000C     64 - LOAD_CONST          -1
                 0000000F     64 - LOAD_CONST          None
                 00000012     6B - IMPORT_NAME         'subprocess'
                 00000015     5A - STORE_NAME          'subprocess'
                 00000018     64 - LOAD_CONST          '\n\n-----------------------------------------------------------------'
                 0000001B     47 - PRINT_ITEM          
                 0000001C     48 - PRINT_NEWLINE       
                 0000001D     64 - LOAD_CONST          'This utility lets you control thresholds on your Thinkpad Battery'
                 00000020     47 - PRINT_ITEM          
                 00000021     48 - PRINT_NEWLINE       
                 00000022     64 - LOAD_CONST          'Disclaimer: I take no responsibility for any damages arising out of'
                 00000025     47 - PRINT_ITEM          
                 00000026     48 - PRINT_NEWLINE       
                 00000027     64 - LOAD_CONST          'the use of of this software. Created by \xe2\x98\xbcJ'
                 0000002A     47 - PRINT_ITEM          
                 0000002B     48 - PRINT_NEWLINE       
                 0000002C     64 - LOAD_CONST          '-----------------------------------------------------------------\n'
                 0000002F     47 - PRINT_ITEM          
                 00000030     48 - PRINT_NEWLINE       
                 00000031     64 - LOAD_CONST          0
                 00000034     5A - STORE_NAME          'flag'
                 00000037     65 - LOAD_NAME           'os'
                 0000003A     69 - LOAD_ATTR           'WEXITSTATUS'
                 0000003D     65 - LOAD_NAME           'os'
                 00000040     69 - LOAD_ATTR           'system'
                 00000043     64 - LOAD_CONST          'dpkg --get-selections | grep tp-smapi-source >> /dev/null'
                 00000046     83 - CALL_FUNCTION       
                 00000049     83 - CALL_FUNCTION       
                 0000004C     64 - LOAD_CONST          0
                 0000004F     6A - COMPARE_OP          "=="
                 00000052     6F - JUMP_IF_FALSE       -> 0000005E
                 00000055     01 - POP_TOP             
                 00000056     64 - LOAD_CONST          'Check tp_smapi...'
                 00000059     47 - PRINT_ITEM          
                 0000005A     48 - PRINT_NEWLINE       
                 0000005B     6E - JUMP_FORWARD        -> 000000A8
                 0000005E     01 - POP_TOP             
                 0000005F     64 - LOAD_CONST          'Installing tp-smapi modules'
                 00000062     47 - PRINT_ITEM          
                 00000063     48 - PRINT_NEWLINE       
                 00000064     65 - LOAD_NAME           'subprocess'
                 00000067     69 - LOAD_ATTR           'Popen'
                 0000006A     64 - LOAD_CONST          'm-a a-i tp-smapi-source'
                 0000006D     64 - LOAD_CONST          'shell'
                 00000070     65 - LOAD_NAME           'True'
                 00000073     64 - LOAD_CONST          'stdout'
                 00000076     65 - LOAD_NAME           'subprocess'
                 00000079     69 - LOAD_ATTR           'PIPE'
                 0000007C     64 - LOAD_CONST          'stderr'
                 0000007F     65 - LOAD_NAME           'subprocess'
                 00000082     69 - LOAD_ATTR           'PIPE'
                 00000085     83 - CALL_FUNCTION       
                 00000088     01 - POP_TOP             
                 00000089     64 - LOAD_CONST          'Loading tp_smapi module'
                 0000008C     47 - PRINT_ITEM          
                 0000008D     48 - PRINT_NEWLINE       
                 0000008E     65 - LOAD_NAME           'os'
                 00000091     69 - LOAD_ATTR           'system'
                 00000094     64 - LOAD_CONST          'modprobe tp_smapi'
                 00000097     83 - CALL_FUNCTION       
                 0000009A     01 - POP_TOP             
                 0000009B     65 - LOAD_NAME           'os'
                 0000009E     69 - LOAD_ATTR           'system'
                 000000A1     64 - LOAD_CONST          'echo tp_smapi >> /etc/modules'
                 000000A4     83 - CALL_FUNCTION       
                 000000A7     01 - POP_TOP             
                 000000A8     65 - LOAD_NAME           'os'
                 000000AB     69 - LOAD_ATTR           'WEXITSTATUS'
                 000000AE     65 - LOAD_NAME           'os'
                 000000B1     69 - LOAD_ATTR           'system'
                 000000B4     64 - LOAD_CONST          'dpkg --get-selections | grep sysfsutils >> /dev/null'
                 000000B7     83 - CALL_FUNCTION       
                 000000BA     83 - CALL_FUNCTION       
                 000000BD     64 - LOAD_CONST          0
                 000000C0     6A - COMPARE_OP          "=="
                 000000C3     6F - JUMP_IF_FALSE       -> 000000CF
                 000000C6     01 - POP_TOP             
                 000000C7     64 - LOAD_CONST          'Check sysfs...'
                 000000CA     47 - PRINT_ITEM          
                 000000CB     48 - PRINT_NEWLINE       
                 000000CC     6E - JUMP_FORWARD        -> 000000E2
                 000000CF     01 - POP_TOP             
                 000000D0     64 - LOAD_CONST          'Installing SysFS Utils'
                 000000D3     47 - PRINT_ITEM          
                 000000D4     48 - PRINT_NEWLINE       
                 000000D5     65 - LOAD_NAME           'os'
                 000000D8     69 - LOAD_ATTR           'system'
                 000000DB     64 - LOAD_CONST          'apt-get -qq install sysfsutils'
                 000000DE     83 - CALL_FUNCTION       
                 000000E1     01 - POP_TOP             
                 000000E2     65 - LOAD_NAME           'os'
                 000000E5     69 - LOAD_ATTR           'WEXITSTATUS'
                 000000E8     65 - LOAD_NAME           'os'
                 000000EB     69 - LOAD_ATTR           'system'
                 000000EE     64 - LOAD_CONST          'grep -q start_charge /etc/sysfs.conf'
                 000000F1     83 - CALL_FUNCTION       
                 000000F4     83 - CALL_FUNCTION       
                 000000F7     64 - LOAD_CONST          0
                 000000FA     6A - COMPARE_OP          "=="
                 000000FD     6F - JUMP_IF_FALSE       -> 00000109
                 00000100     01 - POP_TOP             
                 00000101     64 - LOAD_CONST          'Check tp_smapi in Sysfs...\n'
                 00000104     47 - PRINT_ITEM          
                 00000105     48 - PRINT_NEWLINE       
                 00000106     6E - JUMP_FORWARD        -> 00000129
                 00000109     01 - POP_TOP             
                 0000010A     64 - LOAD_CONST          'Adding tp_smapi thresholds to Sysfs\n\n'
                 0000010D     47 - PRINT_ITEM          
                 0000010E     48 - PRINT_NEWLINE       
                 0000010F     65 - LOAD_NAME           'os'
                 00000112     69 - LOAD_ATTR           'system'
                 00000115     64 - LOAD_CONST          'echo /sys/devices/platform/smapi/BAT0/start_charge_thresh = 100 >>  /etc/sysfs.conf'
                 00000118     83 - CALL_FUNCTION       
                 0000011B     01 - POP_TOP             
                 0000011C     65 - LOAD_NAME           'os'
                 0000011F     69 - LOAD_ATTR           'system'
                 00000122     64 - LOAD_CONST          'echo /sys/devices/platform/smapi/BAT0/stop_charge_thresh = 100 >> /etc/sysfs.conf'
                 00000125     83 - CALL_FUNCTION       
                 00000128     01 - POP_TOP             
                 00000129     64 - LOAD_CONST          '-----------------------------------------------------------'
                 0000012C     47 - PRINT_ITEM          
                 0000012D     48 - PRINT_NEWLINE       
                 0000012E     64 - LOAD_CONST          'Battery(ies) Available:'
                 00000131     47 - PRINT_ITEM          
                 00000132     48 - PRINT_NEWLINE       
                 00000133     65 - LOAD_NAME           'os'
                 00000136     69 - LOAD_ATTR           'WEXITSTATUS'
                 00000139     65 - LOAD_NAME           'os'
                 0000013C     69 - LOAD_ATTR           'system'
                 0000013F     64 - LOAD_CONST          'grep 1 /sys/devices/platform/smapi/BAT0/installed >> /dev/null'
                 00000142     83 - CALL_FUNCTION       
                 00000145     83 - CALL_FUNCTION       
                 00000148     64 - LOAD_CONST          0
                 0000014B     6A - COMPARE_OP          "=="
                 0000014E     6F - JUMP_IF_FALSE       -> 00000192
                 00000151     01 - POP_TOP             
                 00000152     65 - LOAD_NAME           'subprocess'
                 00000155     69 - LOAD_ATTR           'Popen'
                 00000158     64 - LOAD_CONST          'cat /sys/devices/platform/smapi/BAT0/cycle_count'
                 0000015B     64 - LOAD_CONST          'shell'
                 0000015E     65 - LOAD_NAME           'True'
                 00000161     64 - LOAD_CONST          'stdout'
                 00000164     65 - LOAD_NAME           'subprocess'
                 00000167     69 - LOAD_ATTR           'PIPE'
                 0000016A     83 - CALL_FUNCTION       
                 0000016D     5A - STORE_NAME          'cycle0'
                 00000170     65 - LOAD_NAME           'str'
                 00000173     65 - LOAD_NAME           'cycle0'
                 00000176     69 - LOAD_ATTR           'communicate'
                 00000179     83 - CALL_FUNCTION       
                 0000017C     64 - LOAD_CONST          0
                 0000017F     19 - BINARY_SUBSCR       
                 00000180     83 - CALL_FUNCTION       
                 00000183     5A - STORE_NAME          'cycle0'
                 00000186     64 - LOAD_CONST          'Integrated Laptop Battery || Present || Cycle Count: '
                 00000189     65 - LOAD_NAME           'cycle0'
                 0000018C     17 - BINARY_ADD          
                 0000018D     47 - PRINT_ITEM          
                 0000018E     48 - PRINT_NEWLINE       
                 0000018F     6E - JUMP_FORWARD        -> 00000198
                 00000192     01 - POP_TOP             
                 00000193     64 - LOAD_CONST          'Integrated Laptop Battery || Absent  ||'
                 00000196     47 - PRINT_ITEM          
                 00000197     48 - PRINT_NEWLINE       
                 00000198     65 - LOAD_NAME           'os'
                 0000019B     69 - LOAD_ATTR           'WEXITSTATUS'
                 0000019E     65 - LOAD_NAME           'os'
                 000001A1     69 - LOAD_ATTR           'system'
                 000001A4     64 - LOAD_CONST          'grep 1 /sys/devices/platform/smapi/BAT1/installed'
                 000001A7     83 - CALL_FUNCTION       
                 000001AA     83 - CALL_FUNCTION       
                 000001AD     64 - LOAD_CONST          0
                 000001B0     6A - COMPARE_OP          "=="
                 000001B3     6F - JUMP_IF_FALSE       -> 000001F7
                 000001B6     01 - POP_TOP             
                 000001B7     65 - LOAD_NAME           'subprocess'
                 000001BA     69 - LOAD_ATTR           'Popen'
                 000001BD     64 - LOAD_CONST          'cat /sys/devices/platform/smapi/BAT1/cycle_count'
                 000001C0     64 - LOAD_CONST          'shell'
                 000001C3     65 - LOAD_NAME           'True'
                 000001C6     64 - LOAD_CONST          'stdout'
                 000001C9     65 - LOAD_NAME           'subprocess'
                 000001CC     69 - LOAD_ATTR           'PIPE'
                 000001CF     83 - CALL_FUNCTION       
                 000001D2     5A - STORE_NAME          'cycle1'
                 000001D5     65 - LOAD_NAME           'str'
                 000001D8     65 - LOAD_NAME           'cycle1'
                 000001DB     69 - LOAD_ATTR           'communicate'
                 000001DE     83 - CALL_FUNCTION       
                 000001E1     64 - LOAD_CONST          0
                 000001E4     19 - BINARY_SUBSCR       
                 000001E5     83 - CALL_FUNCTION       
                 000001E8     5A - STORE_NAME          'cycle1'
                 000001EB     64 - LOAD_CONST          '-UltraBay Laptop Battery- || Present || Cycle Count: '
                 000001EE     47 - PRINT_ITEM          
                 000001EF     65 - LOAD_NAME           'cycle1'
                 000001F2     47 - PRINT_ITEM          
                 000001F3     48 - PRINT_NEWLINE       
                 000001F4     6E - JUMP_FORWARD        -> 000001FD
                 000001F7     01 - POP_TOP             
                 000001F8     64 - LOAD_CONST          '-UltraBay Laptop Battery- || Absent  ||'
                 000001FB     47 - PRINT_ITEM          
                 000001FC     48 - PRINT_NEWLINE       
                 000001FD     78 - SETUP_LOOP          -> 000003F3
                 00000200     65 - LOAD_NAME           'flag'
                 00000203     64 - LOAD_CONST          1
                 00000206     6A - COMPARE_OP          "!="
                 00000209     6F - JUMP_IF_FALSE       -> 000003F1
                 0000020C     01 - POP_TOP             
                 0000020D     64 - LOAD_CONST          '-----------------------------------------------------------'
                 00000210     47 - PRINT_ITEM          
                 00000211     48 - PRINT_NEWLINE       
                 00000212     64 - LOAD_CONST          'Controlling Integrated Laptop Battery'
                 00000215     47 - PRINT_ITEM          
                 00000216     48 - PRINT_NEWLINE       
                 00000217     64 - LOAD_CONST          '-- -- -- Press -- -- --'
                 0000021A     47 - PRINT_ITEM          
                 0000021B     48 - PRINT_NEWLINE       
                 0000021C     64 - LOAD_CONST          '0 to always charge fully'
                 0000021F     47 - PRINT_ITEM          
                 00000220     48 - PRINT_NEWLINE       
                 00000221     64 - LOAD_CONST          '1 to define % to start battery charging'
                 00000224     47 - PRINT_ITEM          
                 00000225     48 - PRINT_NEWLINE       
                 00000226     64 - LOAD_CONST          '2 to define % to stop battery charging'
                 00000229     47 - PRINT_ITEM          
                 0000022A     48 - PRINT_NEWLINE       
                 0000022B     64 - LOAD_CONST          '3 to view current thresholds'
                 0000022E     47 - PRINT_ITEM          
                 0000022F     48 - PRINT_NEWLINE       
                 00000230     64 - LOAD_CONST          '9 to exit\n'
                 00000233     47 - PRINT_ITEM          
                 00000234     48 - PRINT_NEWLINE       
                 00000235     65 - LOAD_NAME           'input'
                 00000238     64 - LOAD_CONST          'Your choice:'
                 0000023B     83 - CALL_FUNCTION       
                 0000023E     5A - STORE_NAME          'choice'
                 00000241     65 - LOAD_NAME           'choice'
                 00000244     64 - LOAD_CONST          0
                 00000247     6A - COMPARE_OP          "=="
                 0000024A     6F - JUMP_IF_FALSE       -> 00000294
                 0000024D     01 - POP_TOP             
                 0000024E     64 - LOAD_CONST          '\nThe battery will always charge (default setting)'
                 00000251     47 - PRINT_ITEM          
                 00000252     48 - PRINT_NEWLINE       
                 00000253     65 - LOAD_NAME           'os'
                 00000256     69 - LOAD_ATTR           'system'
                 00000259     64 - LOAD_CONST          'echo 100 > /sys/devices/platform/smapi/BAT0/start_charge_thresh'
                 0000025C     83 - CALL_FUNCTION       
                 0000025F     01 - POP_TOP             
                 00000260     65 - LOAD_NAME           'os'
                 00000263     69 - LOAD_ATTR           'system'
                 00000266     64 - LOAD_CONST          'echo 100 > /sys/devices/platform/smapi/BAT0/stop_charge_thresh'
                 00000269     83 - CALL_FUNCTION       
                 0000026C     01 - POP_TOP             
                 0000026D     65 - LOAD_NAME           'os'
                 00000270     69 - LOAD_ATTR           'system'
                 00000273     64 - LOAD_CONST          "sed -i  's|BAT0/start_charge_thresh.*|BAT0/start_charge_thresh = 100|' /etc/sysfs.conf"
                 00000276     83 - CALL_FUNCTION       
                 00000279     01 - POP_TOP             
                 0000027A     65 - LOAD_NAME           'os'
                 0000027D     69 - LOAD_ATTR           'system'
                 00000280     64 - LOAD_CONST          "sed -i  's|BAT0/stop_charge_thresh.*|BAT0/stop_charge_thresh = 100|' /etc/sysfs.conf"
                 00000283     83 - CALL_FUNCTION       
                 00000286     01 - POP_TOP             
                 00000287     65 - LOAD_NAME           'raw_input'
                 0000028A     64 - LOAD_CONST          'Hit ENTER to continue'
                 0000028D     83 - CALL_FUNCTION       
                 00000290     01 - POP_TOP             
                 00000291     71 - JUMP_ABSOLUTE       -> 00000200
                 00000294     01 - POP_TOP             
                 00000295     65 - LOAD_NAME           'choice'
                 00000298     64 - LOAD_CONST          1
                 0000029B     6A - COMPARE_OP          "=="
                 0000029E     6F - JUMP_IF_FALSE       -> 000002EC
                 000002A1     01 - POP_TOP             
                 000002A2     64 - LOAD_CONST          '\nDefine Battery Charge Start Value in Percentage:'
                 000002A5     47 - PRINT_ITEM          
                 000002A6     48 - PRINT_NEWLINE       
                 000002A7     65 - LOAD_NAME           'input'
                 000002AA     83 - CALL_FUNCTION       
                 000002AD     5A - STORE_NAME          'start'
                 000002B0     65 - LOAD_NAME           'os'
                 000002B3     69 - LOAD_ATTR           'system'
                 000002B6     64 - LOAD_CONST          'echo %s > /sys/devices/platform/smapi/BAT0/start_charge_thresh'
                 000002B9     65 - LOAD_NAME           'start'
                 000002BC     16 - BINARY_MODULO       
                 000002BD     83 - CALL_FUNCTION       
                 000002C0     01 - POP_TOP             
                 000002C1     64 - LOAD_CONST          'Battery Lower Limit Set to '
                 000002C4     47 - PRINT_ITEM          
                 000002C5     65 - LOAD_NAME           'start'
                 000002C8     47 - PRINT_ITEM          
                 000002C9     64 - LOAD_CONST          '%'
                 000002CC     47 - PRINT_ITEM          
                 000002CD     48 - PRINT_NEWLINE       
                 000002CE     65 - LOAD_NAME           'os'
                 000002D1     69 - LOAD_ATTR           'system'
                 000002D4     64 - LOAD_CONST          "sed -i  's|BAT0/start_charge_thresh.*|BAT0/start_charge_thresh = %s|' /etc/sysfs.conf"
                 000002D7     65 - LOAD_NAME           'start'
                 000002DA     16 - BINARY_MODULO       
                 000002DB     83 - CALL_FUNCTION       
                 000002DE     01 - POP_TOP             
                 000002DF     65 - LOAD_NAME           'raw_input'
                 000002E2     64 - LOAD_CONST          'Hit ENTER to continue'
                 000002E5     83 - CALL_FUNCTION       
                 000002E8     01 - POP_TOP             
                 000002E9     71 - JUMP_ABSOLUTE       -> 00000200
                 000002EC     01 - POP_TOP             
                 000002ED     65 - LOAD_NAME           'choice'
                 000002F0     64 - LOAD_CONST          2
                 000002F3     6A - COMPARE_OP          "=="
                 000002F6     6F - JUMP_IF_FALSE       -> 00000344
                 000002F9     01 - POP_TOP             
                 000002FA     64 - LOAD_CONST          '\nDefine Battery Charge Stop Value in Percentage:'
                 000002FD     47 - PRINT_ITEM          
                 000002FE     48 - PRINT_NEWLINE       
                 000002FF     65 - LOAD_NAME           'input'
                 00000302     83 - CALL_FUNCTION       
                 00000305     5A - STORE_NAME          'stop'
                 00000308     65 - LOAD_NAME           'os'
                 0000030B     69 - LOAD_ATTR           'system'
                 0000030E     64 - LOAD_CONST          'echo %s > /sys/devices/platform/smapi/BAT0/stop_charge_thresh'
                 00000311     65 - LOAD_NAME           'stop'
                 00000314     16 - BINARY_MODULO       
                 00000315     83 - CALL_FUNCTION       
                 00000318     01 - POP_TOP             
                 00000319     64 - LOAD_CONST          'Battery Upper Limit Set to '
                 0000031C     47 - PRINT_ITEM          
                 0000031D     65 - LOAD_NAME           'stop'
                 00000320     47 - PRINT_ITEM          
                 00000321     64 - LOAD_CONST          '%'
                 00000324     47 - PRINT_ITEM          
                 00000325     48 - PRINT_NEWLINE       
                 00000326     65 - LOAD_NAME           'os'
                 00000329     69 - LOAD_ATTR           'system'
                 0000032C     64 - LOAD_CONST          "sed -i  's|BAT0/stop_charge_thresh.*|BAT0/stop_charge_thresh = %s|' /etc/sysfs.conf"
                 0000032F     65 - LOAD_NAME           'stop'
                 00000332     16 - BINARY_MODULO       
                 00000333     83 - CALL_FUNCTION       
                 00000336     01 - POP_TOP             
                 00000337     65 - LOAD_NAME           'raw_input'
                 0000033A     64 - LOAD_CONST          'Hit ENTER to continue'
                 0000033D     83 - CALL_FUNCTION       
                 00000340     01 - POP_TOP             
                 00000341     71 - JUMP_ABSOLUTE       -> 00000200
                 00000344     01 - POP_TOP             
                 00000345     65 - LOAD_NAME           'choice'
                 00000348     64 - LOAD_CONST          3
                 0000034B     6A - COMPARE_OP          "=="
                 0000034E     6F - JUMP_IF_FALSE       -> 000003E2
                 00000351     01 - POP_TOP             
                 00000352     65 - LOAD_NAME           'subprocess'
                 00000355     69 - LOAD_ATTR           'Popen'
                 00000358     64 - LOAD_CONST          "grep start_charge /etc/sysfs.conf | grep -o '[0-9]\\{2,3\\}' "
                 0000035B     67 - BUILD_LIST          
                 0000035E     64 - LOAD_CONST          'shell'
                 00000361     65 - LOAD_NAME           'True'
                 00000364     64 - LOAD_CONST          'stdout'
                 00000367     65 - LOAD_NAME           'subprocess'
                 0000036A     69 - LOAD_ATTR           'PIPE'
                 0000036D     83 - CALL_FUNCTION       
                 00000370     5A - STORE_NAME          'p_start'
                 00000373     65 - LOAD_NAME           'str'
                 00000376     65 - LOAD_NAME           'p_start'
                 00000379     69 - LOAD_ATTR           'communicate'
                 0000037C     83 - CALL_FUNCTION       
                 0000037F     64 - LOAD_CONST          0
                 00000382     19 - BINARY_SUBSCR       
                 00000383     83 - CALL_FUNCTION       
                 00000386     5A - STORE_NAME          'p_start'
                 00000389     65 - LOAD_NAME           'subprocess'
                 0000038C     69 - LOAD_ATTR           'Popen'
                 0000038F     64 - LOAD_CONST          "grep stop_charge /etc/sysfs.conf | grep -o '[0-9]\\{2,3\\}' "
                 00000392     67 - BUILD_LIST          
                 00000395     64 - LOAD_CONST          'shell'
                 00000398     65 - LOAD_NAME           'True'
                 0000039B     64 - LOAD_CONST          'stdout'
                 0000039E     65 - LOAD_NAME           'subprocess'
                 000003A1     69 - LOAD_ATTR           'PIPE'
                 000003A4     83 - CALL_FUNCTION       
                 000003A7     5A - STORE_NAME          'p_stop'
                 000003AA     65 - LOAD_NAME           'str'
                 000003AD     65 - LOAD_NAME           'p_stop'
                 000003B0     69 - LOAD_ATTR           'communicate'
                 000003B3     83 - CALL_FUNCTION       
                 000003B6     64 - LOAD_CONST          0
                 000003B9     19 - BINARY_SUBSCR       
                 000003BA     83 - CALL_FUNCTION       
                 000003BD     5A - STORE_NAME          'p_stop'
                 000003C0     64 - LOAD_CONST          '\nBattery thresholds for BAT0:- \n\n Charge Start Threshold %:'
                 000003C3     47 - PRINT_ITEM          
                 000003C4     65 - LOAD_NAME           'p_start'
                 000003C7     47 - PRINT_ITEM          
                 000003C8     64 - LOAD_CONST          ' \n Charge Stop Thresholds %:'
                 000003CB     47 - PRINT_ITEM          
                 000003CC     65 - LOAD_NAME           'p_stop'
                 000003CF     47 - PRINT_ITEM          
                 000003D0     64 - LOAD_CONST          '\n'
                 000003D3     47 - PRINT_ITEM          
                 000003D4     48 - PRINT_NEWLINE       
                 000003D5     65 - LOAD_NAME           'raw_input'
                 000003D8     64 - LOAD_CONST          'Hit ENTER to continue'
                 000003DB     83 - CALL_FUNCTION       
                 000003DE     01 - POP_TOP             
                 000003DF     71 - JUMP_ABSOLUTE       -> 00000200
                 000003E2     01 - POP_TOP             
                 000003E3     64 - LOAD_CONST          1
                 000003E6     5A - STORE_NAME          'flag'
                 000003E9     64 - LOAD_CONST          'Good Bye'
                 000003EC     47 - PRINT_ITEM          
                 000003ED     48 - PRINT_NEWLINE       
                 000003EE     71 - JUMP_ABSOLUTE       -> 00000200
                 000003F1     01 - POP_TOP             
                 000003F2     57 - POP_BLOCK           
                 000003F3     64 - LOAD_CONST          None
                 000003F6     53 - RETURN_VALUE        
             consts:
00000415         TUPLE: (
0000041A             INT: -1 (FF FF FF FF),
0000041F             None (4E),
00000420             STR: '\n\n---------------------------------...' (43 00 00 00 0A 0A 2D 2D 2D 2D 2D 2D...),
00000468             STR: 'This utility lets you control thres...' (41 00 00 00 54 68 69 73 20 75 74 69...),
000004AE             STR: 'Disclaimer: I take no responsibilit...' (43 00 00 00 44 69 73 63 6C 61 69 6D...),
000004F6             STR: 'the use of of this software. Create...' (2C 00 00 00 74 68 65 20 75 73 65 20...),
00000527             STR: '-----------------------------------...' (42 00 00 00 2D 2D 2D 2D 2D 2D 2D 2D...),
0000056E             INT: 0 (00 00 00 00),
00000573             STR: 'dpkg --get-selections | grep tp-sma...' (39 00 00 00 64 70 6B 67 20 2D 2D 67...),
000005B1             STR: 'Check tp_smapi...' (11 00 00 00 43 68 65 63 6B 20 74 70...),
000005C7             STR: 'Installing tp-smapi modules' (1B 00 00 00 49 6E 73 74 61 6C 6C 69...),
000005E7             STR: 'm-a a-i tp-smapi-source' (17 00 00 00 6D 2D 61 20 61 2D 69 20...),
00000603             STR: 'shell' (05 00 00 00 73 68 65 6C 6C),
0000060D             STR: 'stdout' (06 00 00 00 73 74 64 6F 75 74),
00000618             STR: 'stderr' (06 00 00 00 73 74 64 65 72 72),
00000623             STR: 'Loading tp_smapi module' (17 00 00 00 4C 6F 61 64 69 6E 67 20...),
0000063F             STR: 'modprobe tp_smapi' (11 00 00 00 6D 6F 64 70 72 6F 62 65...),
00000655             STR: 'echo tp_smapi >> /etc/modules' (1D 00 00 00 65 63 68 6F 20 74 70 5F...),
00000677             STR: 'dpkg --get-selections | grep sysfsu...' (34 00 00 00 64 70 6B 67 20 2D 2D 67...),
000006B0             STR: 'Check sysfs...' (0E 00 00 00 43 68 65 63 6B 20 73 79...),
000006C3             STR: 'Installing SysFS Utils' (16 00 00 00 49 6E 73 74 61 6C 6C 69...),
000006DE             STR: 'apt-get -qq install sysfsutils' (1E 00 00 00 61 70 74 2D 67 65 74 20...),
00000701             STR: 'grep -q start_charge /etc/sysfs.con...' (24 00 00 00 67 72 65 70 20 2D 71 20...),
0000072A             STR: 'Check tp_smapi in Sysfs...\n' (1B 00 00 00 43 68 65 63 6B 20 74 70...),
0000074A             STR: 'Adding tp_smapi thresholds to Sysfs...' (25 00 00 00 41 64 64 69 6E 67 20 74...),
00000774             STR: 'echo /sys/devices/platform/smapi/BA...' (53 00 00 00 65 63 68 6F 20 2F 73 79...),
000007CC             STR: 'echo /sys/devices/platform/smapi/BA...' (51 00 00 00 65 63 68 6F 20 2F 73 79...),
00000822             STR: '-----------------------------------...' (3B 00 00 00 2D 2D 2D 2D 2D 2D 2D 2D...),
00000862             STR: 'Battery(ies) Available:' (17 00 00 00 42 61 74 74 65 72 79 28...),
0000087E             STR: 'grep 1 /sys/devices/platform/smapi/...' (3E 00 00 00 67 72 65 70 20 31 20 2F...),
000008C1             STR: 'cat /sys/devices/platform/smapi/BAT...' (30 00 00 00 63 61 74 20 2F 73 79 73...),
000008F6             STR: 'Integrated Laptop Battery || Presen...' (35 00 00 00 49 6E 74 65 67 72 61 74...),
00000930             STR: 'Integrated Laptop Battery || Absent...' (27 00 00 00 49 6E 74 65 67 72 61 74...),
0000095C             STR: 'grep 1 /sys/devices/platform/smapi/...' (31 00 00 00 67 72 65 70 20 31 20 2F...),
00000992             STR: 'cat /sys/devices/platform/smapi/BAT...' (30 00 00 00 63 61 74 20 2F 73 79 73...),
000009C7             STR: '-UltraBay Laptop Battery- || Presen...' (35 00 00 00 2D 55 6C 74 72 61 42 61...),
00000A01             STR: '-UltraBay Laptop Battery- || Absent...' (27 00 00 00 2D 55 6C 74 72 61 42 61...),
00000A2D             INT: 1 (01 00 00 00),
00000A32             STR: 'Controlling Integrated Laptop Batte...' (25 00 00 00 43 6F 6E 74 72 6F 6C 6C...),
00000A5C             STR: '-- -- -- Press -- -- --' (17 00 00 00 2D 2D 20 2D 2D 20 2D 2D...),
00000A78             STR: '0 to always charge fully' (18 00 00 00 30 20 74 6F 20 61 6C 77...),
00000A95             STR: '1 to define % to start battery char...' (27 00 00 00 31 20 74 6F 20 64 65 66...),
00000AC1             STR: '2 to define % to stop battery charg...' (26 00 00 00 32 20 74 6F 20 64 65 66...),
00000AEC             STR: '3 to view current thresholds' (1C 00 00 00 33 20 74 6F 20 76 69 65...),
00000B0D             STR: '9 to exit\n' (0A 00 00 00 39 20 74 6F 20 65 78 69...),
00000B1C             STR: 'Your choice:' (0C 00 00 00 59 6F 75 72 20 63 68 6F...),
00000B2D             STR: '\nThe battery will always charge (de...' (31 00 00 00 0A 54 68 65 20 62 61 74...),
00000B63             STR: 'echo 100 > /sys/devices/platform/sm...' (3F 00 00 00 65 63 68 6F 20 31 30 30...),
00000BA7             STR: 'echo 100 > /sys/devices/platform/sm...' (3E 00 00 00 65 63 68 6F 20 31 30 30...),
00000BEA             STR: "sed -i  's|BAT0/start_charge_thresh..." (56 00 00 00 73 65 64 20 2D 69 20 20...),
00000C45             STR: "sed -i  's|BAT0/stop_charge_thresh...." (54 00 00 00 73 65 64 20 2D 69 20 20...),
00000C9E             STR: 'Hit ENTER to continue' (15 00 00 00 48 69 74 20 45 4E 54 45...),
00000CB8             STR: '\nDefine Battery Charge Start Value ...' (31 00 00 00 0A 44 65 66 69 6E 65 20...),
00000CEE             STR: 'echo %s > /sys/devices/platform/sma...' (3E 00 00 00 65 63 68 6F 20 25 73 20...),
00000D31             STR: 'Battery Lower Limit Set to ' (1B 00 00 00 42 61 74 74 65 72 79 20...),
00000D51             STR: '%' (01 00 00 00 25),
00000D57             STR: "sed -i  's|BAT0/start_charge_thresh..." (55 00 00 00 73 65 64 20 2D 69 20 20...),
00000DB1             INT: 2 (02 00 00 00),
00000DB6             STR: '\nDefine Battery Charge Stop Value i...' (30 00 00 00 0A 44 65 66 69 6E 65 20...),
00000DEB             STR: 'echo %s > /sys/devices/platform/sma...' (3D 00 00 00 65 63 68 6F 20 25 73 20...),
00000E2D             STR: 'Battery Upper Limit Set to ' (1B 00 00 00 42 61 74 74 65 72 79 20...),
00000E4D             STR: "sed -i  's|BAT0/stop_charge_thresh...." (53 00 00 00 73 65 64 20 2D 69 20 20...),
00000EA5             INT: 3 (03 00 00 00),
00000EAA             STR: 'grep start_charge /etc/sysfs.conf |...' (3B 00 00 00 67 72 65 70 20 73 74 61...),
00000EEA             STR: 'grep stop_charge /etc/sysfs.conf | ...' (3A 00 00 00 67 72 65 70 20 73 74 6F...),
00000F29             STR: '\nBattery thresholds for BAT0:- \n\n C...' (3B 00 00 00 0A 42 61 74 74 65 72 79...),
00000F69             STR: ' \n Charge Stop Thresholds %:' (1C 00 00 00 20 0A 20 43 68 61 72 67...),
00000F8A             STR: '\n' (01 00 00 00 0A),
00000F90             STR: 'Good Bye' (08 00 00 00 47 6F 6F 64 20 42 79 65)
                 )
             names:
00000F9D         TUPLE: (
00000FA2             STR: 'os' (02 00 00 00 6F 73),
00000FA9             STR: 'subprocess' (0A 00 00 00 73 75 62 70 72 6F 63 65...),
00000FB8             STR: 'flag' (04 00 00 00 66 6C 61 67),
00000FC1             STR: 'WEXITSTATUS' (0B 00 00 00 57 45 58 49 54 53 54 41...),
00000FD1             STR: 'system' (06 00 00 00 73 79 73 74 65 6D),
00000FDC             STR: 'Popen' (05 00 00 00 50 6F 70 65 6E),
00000FE6             STR: 'True' (04 00 00 00 54 72 75 65),
00000FEF             STR: 'PIPE' (04 00 00 00 50 49 50 45),
00000FF8             STR: 'cycle0' (06 00 00 00 63 79 63 6C 65 30),
00001003             STR: 'str' (03 00 00 00 73 74 72),
0000100B             STR: 'communicate' (0B 00 00 00 63 6F 6D 6D 75 6E 69 63...),
0000101B             STR: 'cycle1' (06 00 00 00 63 79 63 6C 65 31),
00001026             STR: 'input' (05 00 00 00 69 6E 70 75 74),
00001030             STR: 'choice' (06 00 00 00 63 68 6F 69 63 65),
0000103B             STR: 'raw_input' (09 00 00 00 72 61 77 5F 69 6E 70 75...),
00001049             STR: 'start' (05 00 00 00 73 74 61 72 74),
00001053             STR: 'stop' (04 00 00 00 73 74 6F 70),
0000105C             STR: 'p_start' (07 00 00 00 70 5F 73 74 61 72 74),
00001068             STR: 'p_stop' (06 00 00 00 70 5F 73 74 6F 70)
                 )
             varnames:
00001073         TUPLE: ()
             freevars:
00001078         TUPLE: ()
             cellvars:
0000107D         TUPLE: ()
             filename:
00001082         STR: 'TPTool.py' (09 00 00 00 54 50 54 6F 6F 6C 2E 70...)
             name:
00001090         STR: '<module>' (08 00 00 00 3C 6D 6F 64 75 6C 65 3E)
             firslineno:
0000109D         LONG: 4L (04 00 00 00)
             lnotab:
000010A1         STR: '\x0c\x01\x0c\x01\x05\x01\x05\x01\x05\x01\x05\x01\x05\x01\x06\x02\x1f\x01\t\x02\x05\x01%\x02\x05\x01\r\x01\r\x02\x1f\x01\t\x02\x05...' (98 00 00 00 0C 01 0C 01 05 01 05 01...)

---

### Post by n.l.o on 2011-03-09
It works for me on my T410 2522, but when I reload sysfsutils I get:
```
sudo service sysfsutils restart
* Setting sysfs variables...
* unknown attribute /sys/devices/platform/smapi/BAT0/start_charge_thresh
* unknown attribute /sys/devices/platform/smapi/BAT0/stop_charge_thresh

```

Does this mean that the thresholds are not honored?

I have an extra battery connected (not ultrbay, but a 27++ 9 cell attached to the dock) and I want to make it discharge both of them... and I cannot change the sysfs values it seems, I can run the 
```
echo -n 1 > /sys/devices/platform/smapi/BAT0/force_discharge
```
without error, but nothing changes.
:(

Cheers

---

### Post by jordanStone on 2011-04-22
Were you ever able to get your main battery and your 27++ slice to discharge properly?  I'm thinking of purchasing a 27++ but I want to make sure I can use it properly.

---

### Post by manybodycpa on 2011-05-30
Dear all,

I have an X220 running Natty and the 2.6.39 kernel. I have tried using
the module_assistant to install tp-smapi, but even after this exercise,
I get:

sudo modprobe tp-smapi
FATAL: Error inserting tp_smapi (/lib/modules/2.6.39-0-generic/updates/dkms/tp_smapi.ko): No such device

The module is also not found using lsmod. Any help is appreciated.

> **moixa said:**
> tp_smapi is not longer included as a binary module, though you can still compile it using module-assistant

Install module-assistant, run it, select tp-smapi, then select Build, done!

---

### Post by emeraldgirl08 on 2011-06-01
> **sicvolo said:**
> Yes, try this - sudo aptitude install tp-smapi-dkms

instead of the tp-smapi-source+m-a that the script does.

I ran the script and did not do this on a ThinkPad X200. It shows that it cannot find a battery. How do I remove the "tp-smapi-srouce+m-a" that the script downloaded and install the "tp-smapi-dkms" instead???

I like to set my charge/discharge thresholds manually so I'd like to get this solved. I also haven't dabbled with linux in a long while so I'm green behind the ears again :blush:
 
I'd appreciate any help :)

running 10.04LTS Ubuntu 32-bit

---

### Post by garycahill on 2011-06-01
Did you ever get to the bottom of this ? I have a thinkpad too.

---

### Post by emeraldgirl08 on 2011-06-01
Hi Gary. :)

Give the post a little more time :)

---

### Post by voor on 2011-08-27
Here's the decompiled source.  I haven't tried running it yet, though; waiting for a TP x120e to be delivered.

```
import os
import subprocess
print '\n\n-----------------------------------------------------------------'
print 'This utility lets you control thresholds on your Thinkpad Battery'
print 'Disclaimer: I take no responsibility for any damages arising out of'
print 'the use of of this software. Created by \xe2\x98\xbcJ'
print '-----------------------------------------------------------------\n'
flag = 0
if (os.WEXITSTATUS(os.system('dpkg --get-selections | grep tp-smapi-source >> /dev/null')) == 0):
    print 'Check tp_smapi...'
else:
    print 'Installing tp-smapi modules'
    subprocess.Popen('m-a a-i tp-smapi-source', shell=True, stdout=subprocess.PIPE, stderr=subprocess.PIPE)
    print 'Loading tp_smapi module'
    os.system('modprobe tp_smapi')
    os.system('echo tp_smapi >> /etc/modules')
if (os.WEXITSTATUS(os.system('dpkg --get-selections | grep sysfsutils >> /dev/null')) == 0):
    print 'Check sysfs...'
else:
    print 'Installing SysFS Utils'
    os.system('apt-get -qq install sysfsutils')
if (os.WEXITSTATUS(os.system('grep -q start_charge /etc/sysfs.conf')) == 0):
    print 'Check tp_smapi in Sysfs...\n'
else:
    print 'Adding tp_smapi thresholds to Sysfs\n\n'
    os.system('echo /sys/devices/platform/smapi/BAT0/start_charge_thresh = 100 >>  /etc/sysfs.conf')
    os.system('echo /sys/devices/platform/smapi/BAT0/stop_charge_thresh = 100 >> /etc/sysfs.conf')
print '-----------------------------------------------------------'
print 'Battery(ies) Available:'
if (os.WEXITSTATUS(os.system('grep 1 /sys/devices/platform/smapi/BAT0/installed >> /dev/null')) == 0):
    cycle0 = subprocess.Popen('cat /sys/devices/platform/smapi/BAT0/cycle_count', shell=True, stdout=subprocess.PIPE)
    cycle0 = str(cycle0.communicate()[0])
    print ('Integrated Laptop Battery || Present || Cycle Count: ' + cycle0)
else:
    print 'Integrated Laptop Battery || Absent  ||'
if (os.WEXITSTATUS(os.system('grep 1 /sys/devices/platform/smapi/BAT1/installed')) == 0):
    cycle1 = subprocess.Popen('cat /sys/devices/platform/smapi/BAT1/cycle_count', shell=True, stdout=subprocess.PIPE)
    cycle1 = str(cycle1.communicate()[0])
    print '-UltraBay Laptop Battery- || Present || Cycle Count: ',
    print cycle1
else:
    print '-UltraBay Laptop Battery- || Absent  ||'
while (flag != 1):
    print '-----------------------------------------------------------'
    print 'Controlling Integrated Laptop Battery'
    print '-- -- -- Press -- -- --'
    print '0 to always charge fully'
    print '1 to define % to start battery charging'
    print '2 to define % to stop battery charging'
    print '3 to view current thresholds'
    print '9 to exit\n'
    choice = input('Your choice:')
    if (choice == 0):
        print '\nThe battery will always charge (default setting)'
        os.system('echo 100 > /sys/devices/platform/smapi/BAT0/start_charge_thresh')
        os.system('echo 100 > /sys/devices/platform/smapi/BAT0/stop_charge_thresh')
        os.system("sed -i  's|BAT0/start_charge_thresh.*|BAT0/start_charge_thresh = 100|' /etc/sysfs.conf")
        os.system("sed -i  's|BAT0/stop_charge_thresh.*|BAT0/stop_charge_thresh = 100|' /etc/sysfs.conf")
        raw_input('Hit ENTER to continue')
    elif (choice == 1):
        print '\nDefine Battery Charge Start Value in Percentage:'
        start = input()
        os.system(('echo %s > /sys/devices/platform/smapi/BAT0/start_charge_thresh' % start))
        print 'Battery Lower Limit Set to ',
        print start,
        print '%'
        os.system(("sed -i  's|BAT0/start_charge_thresh.*|BAT0/start_charge_thresh = %s|' /etc/sysfs.conf" % start))
        raw_input('Hit ENTER to continue')
    elif (choice == 2):
        print '\nDefine Battery Charge Stop Value in Percentage:'
        stop = input()
        os.system(('echo %s > /sys/devices/platform/smapi/BAT0/stop_charge_thresh' % stop))
        print 'Battery Upper Limit Set to ',
        print stop,
        print '%'
        os.system(("sed -i  's|BAT0/stop_charge_thresh.*|BAT0/stop_charge_thresh = %s|' /etc/sysfs.conf" % stop))
        raw_input('Hit ENTER to continue')
    elif (choice == 3):
        p_start = subprocess.Popen(["grep start_charge /etc/sysfs.conf | grep -o '[0-9]\\{2,3\\}' "], shell=True, stdout=subprocess.PIPE)
        p_start = str(p_start.communicate()[0])
        p_stop = subprocess.Popen(["grep stop_charge /etc/sysfs.conf | grep -o '[0-9]\\{2,3\\}' "], shell=True, stdout=subprocess.PIPE)
        p_stop = str(p_stop.communicate()[0])
        print '\nBattery thresholds for BAT0:- \n\n Charge Start Threshold %:',
        print p_start,
        print ' \n Charge Stop Thresholds %:',
        print p_stop,
        print '\n'
        raw_input('Hit ENTER to continue')
    else:
        flag = 1
        print 'Good Bye'
```

---

### Post by gabbi on 2013-02-04
Hi, I'd really like to try using this script, but I'm getting the following error when trying to run it:
> 
gabriel@gabriel-laptop:~$ sudo python TPTool-&#9788;J-v0.04.py 
  File "TPTool-&#9788;J-v0.04.py", line 1
SyntaxError: Non-ASCII character '\xd1' in file TPTool-&#9788;J-v0.04.py on line 1, but no encoding declared; see [http://www.python.org/peps/pep-0263.html](http://www.python.org/peps/pep-0263.html) for details


---

### Post by linrunner on 2013-02-04
Hi,

sorry I can't advise you about the script from this thread (btw: it has not been maintained since Nov 2009).  

I suggest you try [TLP]("http://linrunner.de/tlp") to set your ThinkPad's charge thresholds and have many more power saving features.

---

