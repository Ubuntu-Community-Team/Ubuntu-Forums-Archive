---
title: "New Wubi 9.04 (r134RC) is available!"
date: 2009-05-11
forum: Installation &amp; Upgrades
---

### Post by ago on 2009-05-11
Wubi r134 is a new 9.04 release candidate that fixes the issues that have been reported after 9.04 release. It will replace the current 9.04 stand-alone download once fully tested by a wider audience. Wubi r134 is available at: 

[http://people.ubuntu.com/~evand/wubi/jaunty/wubi-r134.exe](http://people.ubuntu.com/~evand/wubi/jaunty/wubi-r134.exe)

Bugs that have been addressed:

[365648: Wubi 9.04 exits without completeing install](https://bugs.edge.launchpad.net/wubi/+bug/365648)
[365642: Wubi 9.04 rev129 fails on error "writelines() argument must be a sequence of strings"](https://bugs.edge.launchpad.net/wubi/+bug/365642)
[365829: Cant install using pre-downloaded iso](https://bugs.edge.launchpad.net/wubi/+bug/365829)
[366009: Wubi exists without error message on corrupt iso image](https://bugs.edge.launchpad.net/wubi/+bug/366009)
[369225: It seems that fat32 filesystem is not identified correctly in some cases](https://bugs.edge.launchpad.net/wubi/+bug/369225)
[373421: Wubi installation did not respect the selected language](https://bugs.edge.launchpad.net/wubi/+bug/373421)
[371264: Erroneous "permission denied" on read error](https://bugs.edge.launchpad.net/wubi/+bug/371264)

I would encourage anyone to use this new version and please report any problem in launchpad: [http://bugs.launchpad.net/wubi/+filebug](http://bugs.launchpad.net/wubi/+filebug)

---

### Post by DemiReticent on 2009-05-19
Can I use Wubi to install the 9.04 netbook remix by transferring the .img file to my netbook?

---

### Post by davidmp_linux on 2009-05-29
> **DemiReticent said:**
> Can I use Wubi to install the 9.04 netbook remix by transferring the .img file to my netbook?

I would like to try that as well, does anyone know if it will work?

---

### Post by lindsay7 on 2009-05-29
NO, Wubi installs under windows and is the full installation of Ubuntu.

---

### Post by victorsxl on 2009-05-30
---

---

### Post by techfanboy81 on 2009-05-31
I'm glad that is available now.  Starting to download.

Thanks.

---

### Post by VoltRabbit on 2009-06-03
Ran this on a older box sporting a amd 2400 proc ATI 9200se video card, and a wireless card of some off brand.  Everything was instantly recognized and ready for use. I enable the shiny compiz features, got my cube on, and connected to the wireless network no problems.

Compliments to the chef/s

---

### Post by techfanboy81 on 2009-06-04
How to install multiple flavors?

---

### Post by Scott M. Sanders on 2009-06-06
I had so much trouble with Wubi in Vista, I simply foregone it and am using VirtualBox with Ubuntu instead. Try it!

---

### Post by lgnokia on 2009-06-13
you have shared nice info about ubuntu,we can get 5 to 8 cds of ubuntu.u know about this?

---

### Post by ago on 2009-06-13
> **techfanboy81 said:**
> How to install multiple flavors?

Install any Ubuntu, then install the other desktop packages from within Ubuntu, you will be able to select the desktop environment when you log-in

---

### Post by ago on 2009-06-13
> **Scott M. Sanders said:**
> I had so much trouble with Wubi in Vista, I simply foregone it and am using VirtualBox with Ubuntu instead. Try it!

Please post a bug as described above if you experience problems, this way the problem can be fixed for other users as well.

---

### Post by techfanboy81 on 2009-06-16
[FONT=Georgia][SIZE=2]**Wubi 9.04** is very easy to install.  The good thing about it,  is that Wubi is created for Windows users and with a single click they can enter into the Linux world.  As I have explore it, its a user friendly installer.  :)
[/SIZE][/FONT]

---

### Post by tylerhayes on 2009-06-23
Is the Ubuntu 9.04 ISO also updated with this new version of Wubi?

---

### Post by ago on 2009-06-23
> **tylerhayes said:**
> Is the Ubuntu 9.04 ISO also updated with this new version of Wubi?

No, you will have to download Wubi separately, regenerating the ISO is a _big_ deal. You can of course run the new Wubi with the "old" ISO.

---

### Post by Scott M. Sanders on 2009-06-23
I'd think having a working Wubi would be a big deal. If anyone cares to post a homemade ISO of such, that'd be nice.

---

### Post by MrJonesiii on 2009-06-27
9.04 ISO won't install at all on my Dell Inspiron 2650 cw 512MB RAM and 1.8Ghz Pentium M. I get to choose the language and then after I select install Ubuntu, I get a flashing underscore in the top left hand corner of the screen and then after about 15 mins that disappears and I see nothing. The CDROM stops spinning, all quiet, no flashing HDD light... 

8.10 installs fine, but when I run all the updates it asks to install, that too goes pear-shaped. If anyone has any ideas as to what I could try to get this sorted, I'd very much appreciate it. 

Would this new version of 9.04 fix the problems I'm seeing here? 

MrJonesiii

---

### Post by buldozerceto on 2009-06-28
Great, thanks, downloading this to try now. Maybe it's stupid question but will it work in vmware with guest win xp?

_______
[Hostgator coupon](http://phpweby.com/hostgator_coupon.php)

---

### Post by wo1fe on 2009-07-09
ok i have tried installing this package. i am currently running jaunty. when it told me that previous installation was detected and i need to uninstall i clicked uninstall only to get what you see below as an error. this was taken from the log file.

07-09 14:12 INFO   CommonBackend: This is the uninstaller running 
07-09 14:12 DEBUG  WindowsFrontend: __init__... 
07-09 14:12 DEBUG  WindowsFrontend: on_init... 
07-09 14:12 INFO   root: Received settings 
07-09 14:12 DEBUG  TaskList: # Running tasklist... 
07-09 14:12 DEBUG  TaskList: ## Running Backup ISO... 
07-09 14:12 DEBUG  TaskList: ## Finished Backup ISO 
07-09 14:12 DEBUG  TaskList: ## Running Remove bootloader entry... 
07-09 14:12 ERROR  WindowsBackend: Cannot find bcdedit 
07-09 14:12 DEBUG  WindowsBackend: undo_bootini C: 
07-09 14:12 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 422910.949219 mb free ntfs) 
07-09 14:12 DEBUG  WindowsBackend: undo_bootini Z: 
07-09 14:12 DEBUG  WindowsBackend: undo_configsys Drive(Z: hd 422910.949219 mb free ntfs) 
07-09 14:12 DEBUG  TaskList: ## Finished Remove bootloader entry 
07-09 14:12 DEBUG  TaskList: ## Running Remove target dir... 
07-09 14:12 DEBUG  CommonBackend: Deleting C:\ubuntu 
07-09 14:12 ERROR  TaskList: [Errno 2] File not found 
Traceback (most recent call last): 
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__ 
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 631, in remove_target_dir 
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\utils.py", line 312, in rm_tree 
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\utils.py", line 55, in run_command 
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\subprocess.py", line 547, in __init__ 
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\subprocess.py", line 701, in _execute_child 
WindowsError: [Errno 2] File not found 
07-09 14:12 DEBUG  TaskList: # Cancelling tasklist 
07-09 14:12 DEBUG  TaskList: # Finished tasklist 
07-09 14:12 ERROR  root: [Errno 2] File not found 
Traceback (most recent call last): 
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run 
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 129, in select_task 
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 142, in run_installer 
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 176, in run_uninstaller 
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks 
WindowsError: [Errno 2] File not found 
07-09 14:12 DEBUG  WindowsFrontend: frontend.on_quit 
07-09 14:12 DEBUG  root: application.on_quit 
07-09 14:12 INFO   root: sys.exit

I honestly have no idea what half this is. but the error is something that should not have occured. does anyone know how to fix this?

---

### Post by miketv4 on 2009-07-10
Get a virus warning:

pla63.tmf.tmp or something

---

### Post by dodoland008 on 2009-07-11
I got this error in windows vista install
[IMG]http://img5.imageshack.us/img5/7254/ubuntuerror.jpg[/IMG]

---

### Post by dodoland008 on 2009-07-11
This is the log file

07-11 00:21 INFO   root: === wubi 9.04 rev134 ===
07-11 00:21 DEBUG  root: Logfile is c:\users\admin\appdata\local\temp\wubi-9.04-rev134.log
07-11 00:21 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\Admin\\Desktop\\wubi-r134.exe"']
07-11 00:21 DEBUG  CommonBackend: data_dir=C:\Users\Admin\AppData\Local\Temp\pylF305.tmp\data
07-11 00:21 DEBUG  WindowsBackend: 7z=C:\Users\Admin\AppData\Local\Temp\pylF305.tmp\bin\7z.exe
07-11 00:21 DEBUG  CommonBackend: Fetching basic info...
07-11 00:21 DEBUG  CommonBackend: original_exe=C:\Users\Admin\Desktop\wubi-r134.exe
07-11 00:21 DEBUG  CommonBackend: platform=win32
07-11 00:21 DEBUG  CommonBackend: osname=nt
07-11 00:21 DEBUG  CommonBackend: language=en_US
07-11 00:21 DEBUG  CommonBackend: encoding=cp1252
07-11 00:21 DEBUG  WindowsBackend: arch=amd64
07-11 00:21 DEBUG  CommonBackend: Parsing isolist=C:\Users\Admin\AppData\Local\Temp\pylF305.tmp\data\isolist.ini
07-11 00:21 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-11 00:21 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-11 00:21 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-11 00:21 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-11 00:21 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-11 00:21 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-11 00:21 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-11 00:21 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-11 00:21 DEBUG  WindowsBackend: Fetching host info...
07-11 00:21 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-11 00:21 DEBUG  WindowsBackend: windows version=vista
07-11 00:21 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Ultimate
07-11 00:21 DEBUG  WindowsBackend: windows_sp=Service Pack 2
07-11 00:21 DEBUG  WindowsBackend: windows_build=6002
07-11 00:21 DEBUG  WindowsBackend: gmt=-5
07-11 00:21 DEBUG  WindowsBackend: country=US
07-11 00:21 DEBUG  WindowsBackend: timezone=America/New_York
07-11 00:21 DEBUG  WindowsBackend: windows_username=Admin
07-11 00:21 DEBUG  WindowsBackend: user_full_name=Admin
07-11 00:21 DEBUG  WindowsBackend: user_directory=C:\Users\Admin
07-11 00:21 DEBUG  WindowsBackend: windows_language_code=1033
07-11 00:21 DEBUG  WindowsBackend: windows_language=English
07-11 00:21 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     E6750  @ 2.66GHz
07-11 00:21 DEBUG  WindowsBackend: bootloader=vista
07-11 00:21 DEBUG  WindowsBackend: system_drive=Drive(C: hd 90705.2929688 mb free ntfs)
07-11 00:21 DEBUG  WindowsBackend: drive=Drive(C: hd 90705.2929688 mb free ntfs)
07-11 00:21 DEBUG  WindowsBackend: drive=Drive(D: hd 126105.53125 mb free ntfs)
07-11 00:21 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free cdfs)
07-11 00:21 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free )
07-11 00:21 DEBUG  WindowsBackend: drive=Drive(H: hd 100060.390625 mb free hfsj)
07-11 00:21 DEBUG  WindowsBackend: drive=Drive(I: hd 124640.339844 mb free hfsj)
07-11 00:21 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free )
07-11 00:21 DEBUG  WindowsBackend: uninstaller_path=None
07-11 00:21 DEBUG  WindowsBackend: previous_target_dir=None
07-11 00:21 DEBUG  WindowsBackend: previous_distro_name=None
07-11 00:21 DEBUG  WindowsBackend: keyboard_id=67699721
07-11 00:21 DEBUG  WindowsBackend: keyboard_layout=us
07-11 00:21 DEBUG  WindowsBackend: keyboard_variant=
07-11 00:21 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
07-11 00:21 DEBUG  CommonBackend: locale=en_US.UTF-8
07-11 00:21 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
07-11 00:21 DEBUG  CommonBackend: Searching ISOs on USB devices
07-11 00:21 DEBUG  CommonBackend: Searching for local CDs
07-11 00:21 DEBUG  Distro:   checking whether C:\Users\Admin\AppData\Local\Temp\pylF305.tmp is a valid Ubuntu CD
07-11 00:21 DEBUG  Distro:     does not contain C:\Users\Admin\AppData\Local\Temp\pylF305.tmp\casper\filesystem.squashfs
07-11 00:21 DEBUG  Distro:   checking whether C:\Users\Admin\AppData\Local\Temp\pylF305.tmp is a valid Ubuntu CD
07-11 00:21 DEBUG  Distro:     does not contain C:\Users\Admin\AppData\Local\Temp\pylF305.tmp\casper\filesystem.squashfs
07-11 00:21 DEBUG  Distro:   checking whether C:\Users\Admin\AppData\Local\Temp\pylF305.tmp is a valid Kubuntu CD
07-11 00:21 DEBUG  Distro:     does not contain C:\Users\Admin\AppData\Local\Temp\pylF305.tmp\casper\filesystem.squashfs
07-11 00:21 DEBUG  Distro:   checking whether C:\Users\Admin\AppData\Local\Temp\pylF305.tmp is a valid Kubuntu CD
07-11 00:21 DEBUG  Distro:     does not contain C:\Users\Admin\AppData\Local\Temp\pylF305.tmp\casper\filesystem.squashfs
07-11 00:21 DEBUG  Distro:   checking whether C:\Users\Admin\AppData\Local\Temp\pylF305.tmp is a valid Xubuntu CD
07-11 00:21 DEBUG  Distro:     does not contain C:\Users\Admin\AppData\Local\Temp\pylF305.tmp\casper\filesystem.squashfs
07-11 00:21 DEBUG  Distro:   checking whether C:\Users\Admin\AppData\Local\Temp\pylF305.tmp is a valid Xubuntu CD
07-11 00:21 DEBUG  Distro:     does not contain C:\Users\Admin\AppData\Local\Temp\pylF305.tmp\casper\filesystem.squashfs
07-11 00:21 DEBUG  Distro:   checking whether C:\Users\Admin\AppData\Local\Temp\pylF305.tmp is a valid Mythbuntu CD
07-11 00:21 DEBUG  Distro:     does not contain C:\Users\Admin\AppData\Local\Temp\pylF305.tmp\casper\filesystem.squashfs
07-11 00:21 DEBUG  Distro:   checking whether C:\Users\Admin\AppData\Local\Temp\pylF305.tmp is a valid Mythbuntu CD
07-11 00:21 DEBUG  Distro:     does not contain C:\Users\Admin\AppData\Local\Temp\pylF305.tmp\casper\filesystem.squashfs
07-11 00:21 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-11 00:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-11 00:21 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-11 00:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-11 00:21 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-11 00:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-11 00:21 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-11 00:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-11 00:21 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-11 00:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-11 00:21 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-11 00:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-11 00:21 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-11 00:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-11 00:21 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-11 00:21 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-11 00:21 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-11 00:21 DEBUG  Distro:   parsing info from str=Ubuntu 8.04 "Hardy Heron" - Release i386 (20080423)
07-11 00:21 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '8.04', 'build': '20080423', 'codename': 'Hardy Heron', 'arch': 'i386'}
07-11 00:21 DEBUG  Distro: wrong version: 8.04 != 9.04
07-11 00:21 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-11 00:21 DEBUG  Distro: wrong version: 8.04 != 9.04
07-11 00:21 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-11 00:21 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
07-11 00:21 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-11 00:21 DEBUG  Distro: wrong name: Ubuntu != Kubuntu
07-11 00:21 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-11 00:21 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
07-11 00:21 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-11 00:21 DEBUG  Distro: wrong name: Ubuntu != Xubuntu
07-11 00:21 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-11 00:21 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
07-11 00:21 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-11 00:21 DEBUG  Distro: wrong name: Ubuntu != Mythbuntu
07-11 00:21 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-11 00:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-11 00:21 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-11 00:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-11 00:21 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-11 00:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-11 00:21 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-11 00:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-11 00:21 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-11 00:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-11 00:21 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-11 00:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-11 00:21 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-11 00:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-11 00:21 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-11 00:21 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-11 00:21 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-11 00:21 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-11 00:21 DEBUG  Distro:   checking whether H:\ is a valid Ubuntu CD
07-11 00:21 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-11 00:21 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
07-11 00:21 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-11 00:21 DEBUG  Distro:   checking whether H:\ is a valid Kubuntu CD
07-11 00:21 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-11 00:21 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
07-11 00:21 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-11 00:21 DEBUG  Distro:   checking whether H:\ is a valid Xubuntu CD
07-11 00:21 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-11 00:21 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
07-11 00:21 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-11 00:21 DEBUG  Distro:   checking whether H:\ is a valid Mythbuntu CD
07-11 00:21 DEBUG  Distro:     does not contain H:\casper\filesystem.squashfs
07-11 00:21 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
07-11 00:21 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-11 00:21 DEBUG  Distro:   checking whether I:\ is a valid Ubuntu CD
07-11 00:21 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-11 00:21 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
07-11 00:21 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-11 00:21 DEBUG  Distro:   checking whether I:\ is a valid Kubuntu CD
07-11 00:21 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-11 00:21 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
07-11 00:21 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-11 00:21 DEBUG  Distro:   checking whether I:\ is a valid Xubuntu CD
07-11 00:21 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-11 00:21 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
07-11 00:21 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-11 00:21 DEBUG  Distro:   checking whether I:\ is a valid Mythbuntu CD
07-11 00:21 DEBUG  Distro:     does not contain I:\casper\filesystem.squashfs
07-11 00:21 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
07-11 00:21 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
07-11 00:21 DEBUG  Distro:   checking whether J:\ is a valid Ubuntu CD
07-11 00:21 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
07-11 00:21 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
07-11 00:21 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
07-11 00:21 DEBUG  Distro:   checking whether J:\ is a valid Kubuntu CD
07-11 00:21 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
07-11 00:21 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
07-11 00:21 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
07-11 00:21 DEBUG  Distro:   checking whether J:\ is a valid Xubuntu CD
07-11 00:21 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
07-11 00:21 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
07-11 00:21 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
07-11 00:21 DEBUG  Distro:   checking whether J:\ is a valid Mythbuntu CD
07-11 00:21 DEBUG  Distro:     does not contain J:\casper\filesystem.squashfs
07-11 00:21 INFO   root: Running the installer...
07-11 00:21 DEBUG  WindowsFrontend: __init__...
07-11 00:21 DEBUG  WindowsFrontend: on_init...
07-11 00:22 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=10000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=hetal
07-11 00:22 INFO   root: Received settings
07-11 00:22 DEBUG  TaskList: # Running tasklist...
07-11 00:22 DEBUG  TaskList: ## Running select_target_dir...
07-11 00:22 INFO   WindowsBackend: Installing into D:\ubuntu
07-11 00:22 DEBUG  TaskList: ## Finished select_target_dir
07-11 00:22 DEBUG  TaskList: ## Running create_dir_structure...
07-11 00:22 DEBUG  CommonBackend: Creating dir D:\ubuntu
07-11 00:22 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
07-11 00:22 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
07-11 00:22 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
07-11 00:22 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
07-11 00:22 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
07-11 00:22 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
07-11 00:22 DEBUG  TaskList: ## Finished create_dir_structure
07-11 00:22 DEBUG  TaskList: ## Running uncompress_target_dir...
07-11 00:22 DEBUG  TaskList: ## Finished uncompress_target_dir
07-11 00:22 DEBUG  TaskList: ## Running create_uninstaller...
07-11 00:22 DEBUG  WindowsBackend: Copying uninstaller C:\Users\Admin\Desktop\wubi-r134.exe -> D:\ubuntu\uninstall-wubi.exe
07-11 00:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
07-11 00:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
07-11 00:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
07-11 00:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
07-11 00:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 9.04-rev134
07-11 00:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
07-11 00:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
07-11 00:22 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
07-11 00:22 DEBUG  TaskList: ## Finished create_uninstaller
07-11 00:22 DEBUG  TaskList: ## Running copy_installation_files...
07-11 00:22 DEBUG  WindowsBackend: Copying C:\Users\Admin\AppData\Local\Temp\pylF305.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
07-11 00:22 DEBUG  WindowsBackend: Copying C:\Users\Admin\AppData\Local\Temp\pylF305.tmp\winboot -> D:\ubuntu\winboot
07-11 00:22 DEBUG  WindowsBackend: Copying C:\Users\Admin\AppData\Local\Temp\pylF305.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
07-11 00:22 DEBUG  TaskList: ## Finished copy_installation_files
07-11 00:22 DEBUG  TaskList: ## Running get_iso...
07-11 00:22 DEBUG  CommonBackend: Searching for local CD
07-11 00:22 DEBUG  Distro:   checking whether C:\Users\Admin\AppData\Local\Temp\pylF305.tmp is a valid Ubuntu CD
07-11 00:22 DEBUG  Distro:     does not contain C:\Users\Admin\AppData\Local\Temp\pylF305.tmp\casper\filesystem.squashfs
07-11 00:22 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-11 00:22 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-11 00:22 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-11 00:22 DEBUG  Distro: wrong version: 8.04 != 9.04
07-11 00:22 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-11 00:22 DEBUG  Distro:   parsing info from str=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
07-11 00:22 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
07-11 00:22 INFO   Distro: Found a valid CD for Ubuntu: F:\
07-11 00:22 DEBUG  TaskList: New task copy_file
07-11 00:22 DEBUG  TaskList: ### Running copy_file...
07-11 00:23 DEBUG  TaskList: ### Finished copy_file
07-11 00:23 DEBUG  TaskList: New task check_iso
07-11 00:23 DEBUG  TaskList: ### Running check_iso...
07-11 00:23 DEBUG  CommonBackend: Checking D:\ubuntu\install\installation.iso
07-11 00:23 DEBUG  Distro:   checking Ubuntu ISO D:\ubuntu\install\installation.iso
07-11 00:23 DEBUG  WindowsBackend:   extracting .disk\info from D:\ubuntu\install\installation.iso
07-11 00:23 DEBUG  Distro:   parsing info from str=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
07-11 00:23 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
07-11 00:23 INFO   Distro: Found a valid iso for Ubuntu: D:\ubuntu\install\installation.iso
07-11 00:23 DEBUG  CommonBackend: Using distro Ubuntu i386 instead of Ubuntu amd64
07-11 00:23 DEBUG  TaskList: New task get_metalink
07-11 00:23 DEBUG  TaskList: #### Running get_metalink...
07-11 00:23 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-i386.metalink](http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-i386.metalink) > D:\ubuntu\install
07-11 00:23 DEBUG  downloader: Download start filename=D:\ubuntu\install\ubuntu-9.04-desktop-i386.metalink, url=http://releases.ubuntu.com/9.04/ubuntu-9.04-desktop-i386.metalink, basename=ubuntu-9.04-desktop-i386.metalink, length=19438, text=None
07-11 00:23 DEBUG  downloader: download finished (read 19438 bytes)
07-11 00:23 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.04/MD5SUMS-metalink](http://releases.ubuntu.com/9.04/MD5SUMS-metalink) > D:\ubuntu\install
07-11 00:23 DEBUG  downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/9.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=413, text=None
07-11 00:23 DEBUG  downloader: download finished (read 413 bytes)
07-11 00:23 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.04/MD5SUMS-metalink.gpg](http://releases.ubuntu.com/9.04/MD5SUMS-metalink.gpg) > D:\ubuntu\install
07-11 00:23 DEBUG  downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/9.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
07-11 00:23 DEBUG  downloader: download finished (read 189 bytes)
07-11 00:23 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
07-11 00:23 INFO   saplog: Checking block bindings..
07-11 00:23 INFO   saplog: Key verified successfully.
07-11 00:23 DEBUG  CommonBackend: metalink md5sums:
1ec553ada3a4a18fb977816ccac02dfc  ubuntu-9.04-alternate-amd64.metalink
5daf9cb57325672f0eb768d6c11888e8  ubuntu-9.04-alternate-i386.metalink
3df58e889d3613abc2347a6b0e8f4d04  ubuntu-9.04-desktop-amd64.metalink
542bc6d7988f1d2967d419c089b08f57  ubuntu-9.04-desktop-i386.metalink
ea0b13f00711ef4b2e5c772482033a1f  ubuntu-9.04-server-amd64.metalink
88e47c579eb587c8aae1a7d7737ab3f0  ubuntu-9.04-server-i386.metalink

07-11 00:23 DEBUG  TaskList: #### Finished get_metalink
07-11 00:23 DEBUG  TaskList: New task get_file_md5
07-11 00:23 DEBUG  TaskList: #### Running get_file_md5...
07-11 00:23 DEBUG  TaskList: #### Finished get_file_md5
07-11 00:23 DEBUG  TaskList: ### Finished check_iso
07-11 00:23 DEBUG  TaskList: ## Finished get_iso
07-11 00:23 DEBUG  TaskList: ## Running extract_kernel...
07-11 00:23 DEBUG  CommonBackend: Copying files from CD F:\
07-11 00:23 DEBUG  CommonBackend: Checking kernel, initrd and md5sums
07-11 00:23 DEBUG  CommonBackend:   checking D:\ubuntu\install\boot\vmlinuz
07-11 00:23 DEBUG  CommonBackend:   D:\ubuntu\install\boot\vmlinuz md5 = da3a16e8bd2392c4eabf52d8fc22e947 == da3a16e8bd2392c4eabf52d8fc22e947
07-11 00:23 DEBUG  CommonBackend:   checking D:\ubuntu\install\boot\initrd.gz
07-11 00:23 DEBUG  CommonBackend:   D:\ubuntu\install\boot\initrd.gz md5 = c0b6de16a3614614b9543ce0f474e63c == c0b6de16a3614614b9543ce0f474e63c
07-11 00:23 DEBUG  TaskList: ## Finished extract_kernel
07-11 00:23 DEBUG  TaskList: ## Running choose_disk_sizes...
07-11 00:23 DEBUG  WindowsBackend: total size=10000
  root=9744
  swap=256
  home=0
  usr=0
07-11 00:23 DEBUG  TaskList: ## Finished choose_disk_sizes
07-11 00:23 DEBUG  TaskList: ## Running create_preseed...
07-11 00:23 DEBUG  TaskList: ## Finished create_preseed
07-11 00:23 DEBUG  TaskList: ## Running modify_bootloader...
07-11 00:23 DEBUG  TaskList: New task modify_bcd
07-11 00:23 DEBUG  TaskList: ### Running modify_bcd...
07-11 00:23 DEBUG  WindowsBackend: modify_bcd Drive(C: hd 90705.2929688 mb free ntfs)
07-11 00:23 ERROR  TaskList: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /create /d Ubuntu /application bootsector
>>retval=1
>>stderr=The boot configuration data store could not be opened.

The requested system device cannot be found.


>>stdout=
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\win32\backend.py", line 626, in modify_bcd
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /create /d Ubuntu /application bootsector
>>retval=1
>>stderr=The boot configuration data store could not be opened.

The requested system device cannot be found.


>>stdout=
07-11 00:23 DEBUG  TaskList: # Cancelling tasklist
07-11 00:23 DEBUG  TaskList: New task modify_bcd
07-11 00:23 ERROR  root: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /create /d Ubuntu /application bootsector
>>retval=1
>>stderr=The boot configuration data store could not be opened.

The requested system device cannot be found.


>>stdout=
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 55, in run
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 129, in select_task
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\application.py", line 155, in run_installer
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\frontends\win32\frontend.py", line 137, in run_tasks
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /create /d Ubuntu /application bootsector
>>retval=1
>>stderr=The boot configuration data store could not be opened.

The requested system device cannot be found.


>>stdout=
07-11 00:23 DEBUG  TaskList: New task modify_bcd
07-11 00:23 DEBUG  TaskList: New task modify_bcd
07-11 00:23 DEBUG  TaskList: ## Finished modify_bootloader
07-11 00:23 DEBUG  TaskList: # Finished tasklist
07-11 00:27 INFO   root: === wubi 9.04 rev134 ===
07-11 00:27 DEBUG  root: Logfile is c:\users\admin\appdata\local\temp\wubi-9.04-rev134.log
07-11 00:27 DEBUG  root: sys.argv = ['main.pyo', '--exefile="D:\\ubuntu\\uninstall-wubi.exe"']
07-11 00:27 DEBUG  CommonBackend: data_dir=C:\Users\Admin\AppData\Local\Temp\pyl2CBB.tmp\data
07-11 00:27 DEBUG  WindowsBackend: 7z=C:\Users\Admin\AppData\Local\Temp\pyl2CBB.tmp\bin\7z.exe
07-11 00:27 DEBUG  CommonBackend: Fetching basic info...
07-11 00:27 DEBUG  CommonBackend: original_exe=D:\ubuntu\uninstall-wubi.exe
07-11 00:27 DEBUG  CommonBackend: platform=win32
07-11 00:27 DEBUG  CommonBackend: osname=nt
07-11 00:27 DEBUG  CommonBackend: language=en_US
07-11 00:27 DEBUG  CommonBackend: encoding=cp1252
07-11 00:27 DEBUG  WindowsBackend: arch=amd64
07-11 00:27 DEBUG  CommonBackend: Parsing isolist=C:\Users\Admin\AppData\Local\Temp\pyl2CBB.tmp\data\isolist.ini
07-11 00:27 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-11 00:27 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-11 00:27 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-11 00:27 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-11 00:27 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-11 00:27 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-11 00:27 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-11 00:27 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-11 00:27 DEBUG  WindowsBackend: Fetching host info...
07-11 00:27 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-11 00:27 DEBUG  WindowsBackend: windows version=vista
07-11 00:27 DEBUG  WindowsBackend: windows_version2=Windows Vista (TM) Ultimate
07-11 00:27 DEBUG  WindowsBackend: windows_sp=Service Pack 2
07-11 00:27 DEBUG  WindowsBackend: windows_build=6002
07-11 00:27 DEBUG  WindowsBackend: gmt=-5
07-11 00:27 DEBUG  WindowsBackend: country=US
07-11 00:27 DEBUG  WindowsBackend: timezone=America/New_York
07-11 00:27 DEBUG  WindowsBackend: windows_username=Admin
07-11 00:27 DEBUG  WindowsBackend: user_full_name=Admin
07-11 00:27 DEBUG  WindowsBackend: user_directory=C:\Users\Admin
07-11 00:27 DEBUG  WindowsBackend: windows_language_code=1033
07-11 00:27 DEBUG  WindowsBackend: windows_language=English
07-11 00:27 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     E6750  @ 2.66GHz
07-11 00:27 DEBUG  WindowsBackend: bootloader=vista
07-11 00:27 DEBUG  WindowsBackend: system_drive=Drive(C: hd 90704.2578125 mb free ntfs)
07-11 00:27 DEBUG  WindowsBackend: drive=Drive(C: hd 90704.2578125 mb free ntfs)
07-11 00:27 DEBUG  WindowsBackend: drive=Drive(D: hd 125393.890625 mb free ntfs)
07-11 00:27 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
07-11 00:27 DEBUG  WindowsBackend: drive=Drive(F: cd 0.0 mb free cdfs)
07-11 00:27 DEBUG  WindowsBackend: drive=Drive(H: hd 100060.390625 mb free hfsj)
07-11 00:27 DEBUG  WindowsBackend: drive=Drive(I: hd 124640.339844 mb free hfsj)
07-11 00:27 DEBUG  WindowsBackend: drive=Drive(J: cd 0.0 mb free )
07-11 00:27 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
07-11 00:27 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
07-11 00:27 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
07-11 00:27 DEBUG  WindowsBackend: keyboard_id=67699721
07-11 00:27 DEBUG  WindowsBackend: keyboard_layout=us
07-11 00:27 DEBUG  WindowsBackend: keyboard_variant=
07-11 00:27 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
07-11 00:27 DEBUG  CommonBackend: locale=en_US.UTF-8
07-11 00:27 DEBUG  WindowsBackend: total_memory_mb=2047.99999905
07-11 00:27 DEBUG  CommonBackend: Searching ISOs on USB devices
07-11 00:27 DEBUG  CommonBackend: Searching for local CDs
07-11 00:27 DEBUG  Distro:   checking whether C:\Users\Admin\AppData\Local\Temp\pyl2CBB.tmp is a valid Ubuntu CD
07-11 00:27 DEBUG  Distro:     does not contain C:\Users\Admin\AppData\Local\Temp\pyl2CBB.tmp\casper\filesystem.squashfs
07-11 00:27 DEBUG  Distro:   checking whether C:\Users\Admin\AppData\Local\Temp\pyl2CBB.tmp is a valid Ubuntu CD
07-11 00:27 DEBUG  Distro:     does not contain C:\Users\Admin\AppData\Local\Temp\pyl2CBB.tmp\casper\filesystem.squashfs
07-11 00:27 DEBUG  Distro:   checking whether C:\Users\Admin\AppData\Local\Temp\pyl2CBB.tmp is a valid Kubuntu CD
07-11 00:27 DEBUG  Distro:     does not contain C:\Users\Admin\AppData\Local\Temp\pyl2CBB.tmp\casper\filesystem.squashfs
07-11 00:27 DEBUG  Distro:   checking whether C:\Users\Admin\AppData\Local\Temp\pyl2CBB.tmp is a valid Kubuntu CD
07-11 00:27 DEBUG  Distro:     does not contain C:\Users\Admin\AppData\Local\Temp\pyl2CBB.tmp\casper\filesystem.squashfs
07-11 00:27 DEBUG  Distro:   checking whether C:\Users\Admin\AppData\Local\Temp\pyl2CBB.tmp is a valid Xubuntu CD
07-11 00:27 DEBUG  Distro:     does not contain C:\Users\Admin\AppData\Local\Temp\pyl2CBB.tmp\casper\filesystem.squashfs
07-11 00:27 DEBUG  Distro:   checking whether C:\Users\Admin\AppData\Local\Temp\pyl2CBB.tmp is a valid Xubuntu CD
07-11 00:27 DEBUG  Distro:     does not contain C:\Users\Admin\AppData\Local\Temp\pyl2CBB.tmp\casper\filesystem.squashfs
07-11 00:27 DEBUG  Distro:   checking whether C:\Users\Admin\AppData\Local\Temp\pyl2CBB.tmp is a valid Mythbuntu CD
07-11 00:27 DEBUG  Distro:     does not contain C:\Users\Admin\AppData\Local\Temp\pyl2CBB.tmp\casper\filesystem.squashfs
07-11 00:27 DEBUG  Distro:   checking whether C:\Users\Admin\AppData\Local\Temp\pyl2CBB.tmp is a valid Mythbuntu CD
07-11 00:27 DEBUG  Distro:     does not contain C:\Users\Admin\AppData\Local\Temp\pyl2CBB.tmp\casper\filesystem.squashfs
07-11 00:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-11 00:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-11 00:27 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-11 00:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-11 00:27 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-11 00:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-11 00:27 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-11 00:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-11 00:27 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-11 00:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-11 00:27 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-11 00:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-11 00:27 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-11 00:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-11 00:27 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-11 00:27 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-11 00:27 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-11 00:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-11 00:27 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-11 00:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-11 00:27 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-11 00:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-11 00:27 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-11 00:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-11 00:27 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-11 00:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-11 00:27 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-11 00:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-11 00:27 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-11 00:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-11 00:27 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-11 00:27 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-11 00:27 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-11 00:27 DEBUG  Distro:   parsing info from str=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
07-11 00:27 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
07-11 00:27 INFO   Distro: Found a valid CD for Ubuntu: F:\
07-11 00:27 INFO   root: Running the uninstaller...
07-11 00:27 INFO   CommonBackend: This is the uninstaller running
07-11 00:27 DEBUG  WindowsFrontend: __init__...
07-11 00:27 DEBUG  WindowsFrontend: on_init...
07-11 00:27 INFO   root: Received settings
07-11 00:27 DEBUG  TaskList: # Running tasklist...
07-11 00:27 DEBUG  TaskList: ## Running Backup ISO...
07-11 00:27 DEBUG  TaskList: ## Finished Backup ISO
07-11 00:27 DEBUG  TaskList: ## Running Remove bootloader entry...
07-11 00:27 DEBUG  WindowsBackend: Could not find bcd id
07-11 00:27 DEBUG  WindowsBackend: undo_bootini C:
07-11 00:27 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 90704.2578125 mb free ntfs)
07-11 00:27 DEBUG  WindowsBackend: undo_bootini D:
07-11 00:27 DEBUG  WindowsBackend: undo_configsys Drive(D: hd 125393.890625 mb free ntfs)
07-11 00:27 DEBUG  WindowsBackend: undo_bootini H:
07-11 00:27 DEBUG  WindowsBackend: undo_configsys Drive(H: hd 100060.390625 mb free hfsj)
07-11 00:27 DEBUG  WindowsBackend: undo_bootini I:
07-11 00:27 DEBUG  WindowsBackend: undo_configsys Drive(I: hd 124640.339844 mb free hfsj)
07-11 00:27 DEBUG  TaskList: ## Finished Remove bootloader entry
07-11 00:27 DEBUG  TaskList: ## Running Remove target dir...
07-11 00:27 DEBUG  CommonBackend: Deleting D:\ubuntu
07-11 00:27 DEBUG  TaskList: ## Finished Remove target dir
07-11 00:27 DEBUG  TaskList: ## Running Remove registry key...
07-11 00:27 DEBUG  TaskList: ## Finished Remove registry key
07-11 00:27 DEBUG  TaskList: # Finished tasklist
07-11 00:27 INFO   root: Almost finished uninstalling
07-11 00:27 INFO   root: Finished uninstallation
07-11 00:27 DEBUG  root: application.quit
07-11 00:27 DEBUG  WindowsFrontend: frontend.quit
07-11 00:27 DEBUG  WindowsFrontend: frontend.on_quit
07-11 00:27 DEBUG  root: application.on_quit
07-11 00:27 INFO   root: sys.exit

---

### Post by sittnduck on 2009-07-11
07-11 02:56 DEBUG  TaskList: New task check_iso
07-11 02:56 DEBUG  CommonBackend: Searching for local ISO
07-11 02:56 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
07-11 02:56 DEBUG  TaskList: New task get_metalink
07-11 02:56 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\tasklist.py", line 196, in __call__
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 487, in get_iso
  File "Z:\home\evan\bzr\wubi.trunk\build\wubi\files\lib\wubi\backends\common\backend.py", line 326, in download_iso
Exception: Cannot download the metalink and therefore the ISO
07-11 02:56 DEBUG  TaskList: # Cancelling tasklist
07-11 02:56 DEBUG  TaskList: # Finished tasklist
07-11 03:00 INFO   root: === wubi 9.04 rev134 ===
07-11 03:00 DEBUG  root: Logfile is c:\users\sittnd~1\appdata\local\temp\wubi-9.04-rev134.log
07-11 03:00 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\sittnduck\\Desktop\\ubuntu\\wubi-r134.exe"']
07-11 03:00 DEBUG  CommonBackend: data_dir=C:\Users\SITTND~1\AppData\Local\Temp\pylEFFA.tmp\data
07-11 03:00 DEBUG  WindowsBackend: 7z=C:\Users\SITTND~1\AppData\Local\Temp\pylEFFA.tmp\bin\7z.exe
07-11 03:00 DEBUG  CommonBackend: Fetching basic info...
07-11 03:00 DEBUG  CommonBackend: original_exe=C:\Users\sittnduck\Desktop\ubuntu\wubi-r134.exe
07-11 03:00 DEBUG  CommonBackend: platform=win32
07-11 03:00 DEBUG  CommonBackend: osname=nt
07-11 03:00 DEBUG  CommonBackend: language=en_US
07-11 03:00 DEBUG  CommonBackend: encoding=cp1252
07-11 03:00 DEBUG  WindowsBackend: arch=amd64
07-11 03:00 DEBUG  CommonBackend: Parsing isolist=C:\Users\SITTND~1\AppData\Local\Temp\pylEFFA.tmp\data\isolist.ini
07-11 03:00 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-11 03:00 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-11 03:00 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-11 03:00 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-11 03:00 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-11 03:00 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-11 03:00 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-11 03:00 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-11 03:00 DEBUG  WindowsBackend: Fetching host info...
07-11 03:00 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-11 03:00 DEBUG  WindowsBackend: windows version=vista
07-11 03:00 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
07-11 03:00 DEBUG  WindowsBackend: windows_sp=None
07-11 03:00 DEBUG  WindowsBackend: windows_build=7100
07-11 03:00 DEBUG  WindowsBackend: gmt=-6
07-11 03:00 DEBUG  WindowsBackend: country=US
07-11 03:00 DEBUG  WindowsBackend: timezone=America/Chicago
07-11 03:00 DEBUG  WindowsBackend: windows_username=sittnduck
07-11 03:00 DEBUG  WindowsBackend: user_full_name=sittnduck
07-11 03:00 DEBUG  WindowsBackend: user_directory=C:\Users\sittnduck
07-11 03:00 DEBUG  WindowsBackend: windows_language_code=1033
07-11 03:00 DEBUG  WindowsBackend: windows_language=English
07-11 03:00 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU    Q6700  @ 2.66GHz
07-11 03:00 DEBUG  WindowsBackend: bootloader=vista
07-11 03:00 DEBUG  WindowsBackend: system_drive=Drive(C: hd 327228.761719 mb free ntfs)
07-11 03:00 DEBUG  WindowsBackend: drive=Drive(C: hd 327228.761719 mb free ntfs)
07-11 03:00 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
07-11 03:00 DEBUG  WindowsBackend: drive=Drive(E: hd 109341.921875 mb free ntfs)
07-11 03:00 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
07-11 03:00 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
07-11 03:00 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
07-11 03:00 DEBUG  WindowsBackend: keyboard_id=67699721
07-11 03:00 DEBUG  WindowsBackend: keyboard_layout=us
07-11 03:00 DEBUG  WindowsBackend: keyboard_variant=
07-11 03:00 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
07-11 03:00 DEBUG  CommonBackend: locale=en_US.UTF-8
07-11 03:00 DEBUG  WindowsBackend: total_memory_mb=4094.5390625
07-11 03:00 DEBUG  CommonBackend: Searching ISOs on USB devices
07-11 03:00 DEBUG  CommonBackend: Searching for local CDs
07-11 03:00 DEBUG  Distro:   checking whether C:\Users\SITTND~1\AppData\Local\Temp\pylEFFA.tmp is a valid Ubuntu CD
07-11 03:00 DEBUG  Distro:     does not contain C:\Users\SITTND~1\AppData\Local\Temp\pylEFFA.tmp\casper\filesystem.squashfs
07-11 03:00 DEBUG  Distro:   checking whether C:\Users\SITTND~1\AppData\Local\Temp\pylEFFA.tmp is a valid Ubuntu CD
07-11 03:00 DEBUG  Distro:     does not contain C:\Users\SITTND~1\AppData\Local\Temp\pylEFFA.tmp\casper\filesystem.squashfs
07-11 03:00 DEBUG  Distro:   checking whether C:\Users\SITTND~1\AppData\Local\Temp\pylEFFA.tmp is a valid Kubuntu CD
07-11 03:00 DEBUG  Distro:     does not contain C:\Users\SITTND~1\AppData\Local\Temp\pylEFFA.tmp\casper\filesystem.squashfs
07-11 03:00 DEBUG  Distro:   checking whether C:\Users\SITTND~1\AppData\Local\Temp\pylEFFA.tmp is a valid Kubuntu CD
07-11 03:00 DEBUG  Distro:     does not contain C:\Users\SITTND~1\AppData\Local\Temp\pylEFFA.tmp\casper\filesystem.squashfs
07-11 03:00 DEBUG  Distro:   checking whether C:\Users\SITTND~1\AppData\Local\Temp\pylEFFA.tmp is a valid Xubuntu CD
07-11 03:00 DEBUG  Distro:     does not contain C:\Users\SITTND~1\AppData\Local\Temp\pylEFFA.tmp\casper\filesystem.squashfs
07-11 03:00 DEBUG  Distro:   checking whether C:\Users\SITTND~1\AppData\Local\Temp\pylEFFA.tmp is a valid Xubuntu CD
07-11 03:00 DEBUG  Distro:     does not contain C:\Users\SITTND~1\AppData\Local\Temp\pylEFFA.tmp\casper\filesystem.squashfs
07-11 03:00 DEBUG  Distro:   checking whether C:\Users\SITTND~1\AppData\Local\Temp\pylEFFA.tmp is a valid Mythbuntu CD
07-11 03:00 DEBUG  Distro:     does not contain C:\Users\SITTND~1\AppData\Local\Temp\pylEFFA.tmp\casper\filesystem.squashfs
07-11 03:00 DEBUG  Distro:   checking whether C:\Users\SITTND~1\AppData\Local\Temp\pylEFFA.tmp is a valid Mythbuntu CD
07-11 03:00 DEBUG  Distro:     does not contain C:\Users\SITTND~1\AppData\Local\Temp\pylEFFA.tmp\casper\filesystem.squashfs
07-11 03:00 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-11 03:00 DEBUG  Distro:   parsing info from str=Ubuntu 9.04 "Jaunty Jackalope" - Release i386 (20090420.1)
07-11 03:00 DEBUG  Distro:   parsed info={'name': 'Ubuntu', 'subversion': 'Release', 'version': '9.04', 'build': '20090420.1', 'codename': 'Jaunty Jackalope', 'arch': 'i386'}
07-11 03:00 INFO   Distro: Found a valid CD for Ubuntu: D:\
07-11 03:00 INFO   root: Running the CD menu...
07-11 03:00 DEBUG  WindowsFrontend: __init__...
07-11 03:00 DEBUG  WindowsFrontend: on_init...
07-11 03:01 INFO   root: CD menu finished
07-11 03:01 INFO   root: Already installed, running the uninstaller...
07-11 03:01 INFO   root: Running the uninstaller...
07-11 03:01 INFO   CommonBackend: This is the uninstaller running
07-11 03:01 INFO   root: Received settings
07-11 03:01 DEBUG  TaskList: # Running tasklist...
07-11 03:01 DEBUG  TaskList: ## Running Backup ISO...
07-11 03:01 DEBUG  TaskList: ## Finished Backup ISO
07-11 03:01 DEBUG  TaskList: ## Running Remove bootloader entry...
07-11 03:01 DEBUG  WindowsBackend: Could not find bcd id
07-11 03:01 DEBUG  WindowsBackend: undo_bootini C:
07-11 03:01 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 327228.761719 mb free ntfs)
07-11 03:01 DEBUG  WindowsBackend: undo_bootini E:
07-11 03:01 DEBUG  WindowsBackend: undo_configsys Drive(E: hd 109341.921875 mb free ntfs)
07-11 03:01 DEBUG  TaskList: ## Finished Remove bootloader entry
07-11 03:01 DEBUG  TaskList: ## Running Remove target dir...
07-11 03:01 DEBUG  CommonBackend: Deleting C:\ubuntu
07-11 03:01 DEBUG  TaskList: ## Finished Remove target dir
07-11 03:01 DEBUG  TaskList: ## Running Remove registry key...
07-11 03:01 DEBUG  TaskList: ## Finished Remove registry key
07-11 03:01 DEBUG  TaskList: # Finished tasklist
07-11 03:01 INFO   root: Almost finished uninstalling
07-11 03:01 INFO   root: Finished uninstallation
07-11 03:01 DEBUG  CommonBackend: Fetching basic info...
07-11 03:01 DEBUG  CommonBackend: original_exe=C:\Users\sittnduck\Desktop\ubuntu\wubi-r134.exe
07-11 03:01 DEBUG  CommonBackend: platform=win32
07-11 03:01 DEBUG  CommonBackend: osname=nt
07-11 03:01 DEBUG  CommonBackend: language=en_US
07-11 03:01 DEBUG  CommonBackend: encoding=cp1252
07-11 03:01 DEBUG  WindowsBackend: arch=amd64
07-11 03:01 DEBUG  CommonBackend: Parsing isolist=C:\Users\SITTND~1\AppData\Local\Temp\pylEFFA.tmp\data\isolist.ini
07-11 03:01 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-11 03:01 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-11 03:01 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-11 03:01 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-11 03:01 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-11 03:01 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-11 03:01 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-11 03:01 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-11 03:01 DEBUG  WindowsBackend: Fetching host info...
07-11 03:01 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-11 03:01 DEBUG  WindowsBackend: windows version=vista
07-11 03:01 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
07-11 03:01 DEBUG  WindowsBackend: windows_sp=None
07-11 03:01 DEBUG  WindowsBackend: windows_build=7100
07-11 03:01 DEBUG  WindowsBackend: gmt=-6
07-11 03:01 DEBUG  WindowsBackend: country=US
07-11 03:01 DEBUG  WindowsBackend: timezone=America/Chicago
07-11 03:01 DEBUG  WindowsBackend: windows_username=sittnduck
07-11 03:01 DEBUG  WindowsBackend: user_full_name=sittnduck
07-11 03:01 DEBUG  WindowsBackend: user_directory=C:\Users\sittnduck
07-11 03:01 DEBUG  WindowsBackend: windows_language_code=1033
07-11 03:01 DEBUG  WindowsBackend: windows_language=English
07-11 03:01 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Quad CPU    Q6700  @ 2.66GHz
07-11 03:01 DEBUG  WindowsBackend: bootloader=vista
07-11 03:01 DEBUG  WindowsBackend: system_drive=Drive(C: hd 327928.671875 mb free ntfs)
07-11 03:01 DEBUG  WindowsBackend: drive=Drive(C: hd 327928.671875 mb free ntfs)
07-11 03:01 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free cdfs)
07-11 03:01 DEBUG  WindowsBackend: drive=Drive(E: hd 109341.921875 mb free ntfs)
07-11 03:01 DEBUG  WindowsBackend: uninstaller_path=None
07-11 03:01 DEBUG  WindowsBackend: previous_target_dir=None
07-11 03:01 DEBUG  WindowsBackend: previous_distro_name=None
07-11 03:01 DEBUG  WindowsBackend: keyboard_id=67699721
07-11 03:01 DEBUG  WindowsBackend: keyboard_layout=us
07-11 03:01 DEBUG  WindowsBackend: keyboard_variant=
07-11 03:01 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
07-11 03:01 DEBUG  CommonBackend: locale=en_US.UTF-8
07-11 03:01 DEBUG  WindowsBackend: total_memory_mb=4094.5390625
07-11 03:01 DEBUG  CommonBackend: Searching ISOs on USB devices
07-11 03:01 DEBUG  CommonBackend: Searching for local CDs
07-11 03:01 DEBUG  Distro:   checking whether C:\Users\SITTND~1\AppData\Local\Temp\pylEFFA.tmp is a valid Ubuntu CD
07-11 03:01 DEBUG  Distro:     does not contain C:\Users\SITTND~1\AppData\Local\Temp\pylEFFA.tmp\casper\filesystem.squashfs
07-11 03:01 DEBUG  Distro:   checking whether C:\Users\SITTND~1\AppData\Local\Temp\pylEFFA.tmp is a valid Ubuntu CD
07-11 03:01 DEBUG  Distro:     does not contain C:\Users\SITTND~1\AppData\Local\Temp\pylEFFA.tmp\casper\filesystem.squashfs
07-11 03:01 DEBUG  Distro:   checking whether C:\Users\SITTND~1\AppData\Local\Temp\pylEFFA.tmp is a valid Kubuntu CD
07-11 03:01 DEBUG  Distro:     does not contain C:\Users\SITTND~1\AppData\Local\Temp\pylEFFA.tmp\casper\filesystem.squashfs
07-11 03:01 DEBUG  Distro:   checking whether C:\Users\SITTND~1\AppData\Local\Temp\pylEFFA.tmp is a valid Kubuntu CD
07-11 03:01 DEBUG  Distro:     does not contain C:\Users\SITTND~1\AppData\Local\Temp\pylEFFA.tmp\casper\filesystem.squashfs
07-11 03:01 DEBUG  Distro:   checking whether C:\Users\SITTND~1\AppData\Local\Temp\pylEFFA.tmp is a valid Xubuntu CD
07-11 03:01 DEBUG  Distro:     does not contain C:\Users\SITTND~1\AppData\Local\Temp\pylEFFA.tmp\casper\filesystem.squashfs
07-11 03:01 DEBUG  Distro:   checking whether C:\Users\SITTND~1\AppData\Local\Temp\pylEFFA.tmp is a valid Xubuntu CD
07-11 03:01 DEBUG  Distro:     does not contain C:\Users\SITTND~1\AppData\Local\Temp\pylEFFA.tmp\casper\filesystem.squashfs
07-11 03:01 DEBUG  Distro:   checking whether C:\Users\SITTND~1\AppData\Local\Temp\pylEFFA.tmp is a valid Mythbuntu CD
07-11 03:01 DEBUG  Distro:     does not contain C:\Users\SITTND~1\AppData\Local\Temp\pylEFFA.tmp\casper\filesystem.squashfs
07-11 03:01 DEBUG  Distro:   checking whether C:\Users\SITTND~1\AppData\Local\Temp\pylEFFA.tmp is a valid Mythbuntu CD
07-11 03:01 DEBUG  Distro:     does not contain C:\Users\SITTND~1\AppData\Local\Temp\pylEFFA.tmp\casper\filesystem.squashfs
07-11 03:01 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-11 03:01 INFO   Distro: Found a valid CD for Ubuntu: D:\
07-11 03:01 INFO   root: Running the installer...
07-11 03:01 INFO   WindowsFrontend: Operation cancelled
07-11 03:01 DEBUG  WindowsFrontend: frontend.quit
07-11 03:01 DEBUG  WindowsFrontend: frontend.on_quit
07-11 03:01 DEBUG  root: application.on_quit
07-11 03:01 INFO   root: sys.exit

---

### Post by Rafael Dreux on 2009-07-11
Hi please, I'm trying to install Ubuntu in Windows by wubi, but I can't, it says to log the file: C:\Documents and Settings\rafael\Configurações locais\temp\wubi.....log. 
I have a computer with Windows XP, 512 mb RAM, Intel processor.

If someone can help me, please leave a message.

Thanks, Rafael.

---

### Post by Rafael Dreux on 2009-07-11
Hi everyone, just tell me one thing, I need to be in Ubuntu to use wuby to instal Ubuntu inside windows? Or I can be in Windows?

Thanks, Rafael.

---

### Post by Rafael Dreux on 2009-07-11
[IMG]file:///C:/DOCUME%7E1/Rafael/CONFIG%7E1/Temp/moz-screenshot.jpg[/IMG][IMG]file:///C:/DOCUME%7E1/Rafael/CONFIG%7E1/Temp/moz-screenshot-1.jpg[/IMG][IMG]file:///C:/DOCUME%7E1/Rafael/CONFIG%7E1/Temp/moz-screenshot-2.jpg[/IMG]This is the error that is happening.
Please help me.

---

### Post by fast-Eddie on 2009-07-12
Can Wubi install the 64 bit version as well or only the 32 bit version?? I tried installing wubi but didn't go through with it as it didn't give me an option to install the 64 bit version. Can someone pls confirm??

THanks

---

### Post by Scott M. Sanders on 2009-07-12
You can download the 64-bit ISO and run this Wubi with it.

---

### Post by sittnduck on 2009-07-14
Has anyone been successful in installing the 64 bit inside windows 7 yet? I have tried the 32 bit and 64 bit and I still get an error, and the r134rc does not finish. I've noticed several postings along with mine concerning the issue, but no answers as of yet. Anyone found a work-a-round?

Thanks.

---

### Post by sittnduck on 2009-07-14
oops, it works just fine. I was making a local copy of the extracted ISO, once I used the new r134rc exe file and left the ISO alone, it worked fine. Good work, Ubuntu team.

---

### Post by xnsine on 2009-07-16
Does this version of wubi work on software or "fake" raid SATA drives?

---

### Post by Havoca on 2009-07-20
Thanks , Really Great

---

### Post by sallyshaw on 2009-07-22
I have just installed WUBI, all is well but when I reboot to the dual boot to select OP, the keyboard does not work to select any option. My keyboard/mouse is TRUST USB wireless. 
I didn't have this problem before I installed WUBI.
Can anyone help please?:(

---

### Post by stlsaint on 2009-07-24
> **buldozerceto said:**
> Great, thanks, downloading this to try now. Maybe it's stupid question but will it work in vmware with guest win xp?

_______
[Hostgator coupon](http://phpweby.com/hostgator_coupon.php)

well considering that vmware is installed thru an iso or any image you will probably have to install on older version first then attempt to upgrade from the newer wubi from a newer iso image!

---

### Post by racie on 2009-07-26
Here is an error I've found. [http://ubuntuforums.org/showthread.php?t=1223856](http://ubuntuforums.org/showthread.php?t=1223856)

Sorry, I don't know how to report it to that site.

---

### Post by adromidon on 2009-08-09
Attached is a screen shot of an error message I get when trying to run the WUbi installed 9.04 r134RC and the stable one under the latest.php script as of today.

If i hit cancel eventualy it will load the wubi interface but i have to hit it several times like 10 

This happens every single time i try to run it

---

### Post by legendbb on 2009-08-17
I'm having same situation of not been about to run WUBI under XP SP3

reported:
[http://ubuntuforums.org/showthread.php?t=1137395](http://ubuntuforums.org/showthread.php?t=1137395)

Thanks,

---

### Post by yzfvie on 2009-08-20
I am new to UBUNTU and wanted to try it out. I installed UBUNTU a few days ago and started with 8.10 and upgraded to 9.04. I started installing a couple of applications.

After trying to install these applications, I started getting error messages that some application components were not running properly(can't remember anymore). I turned off the computer for the day and when I rebooted the next day, all I had was the desktop screen without the taskbars. The only thing I can do is Cntl-alt-del to turn off the computer and the right mouse button opens a box with options (Create folder,launcher or document) and (Change desktop background)

Is there anything I can do to restore my taskbar short of re-installing UBUNTU?

Thanks.

---

### Post by Shaba1 on 2009-08-21
I just discovered WUBI about two weeks ago. Its VERY interesting for a windows person like me. My question is: Can Wubi or the method that Wubi uses be used with any other linux distro? Specifically I would like to install BACKTRACK 4 in this same way. I am a novice penetration and security tester so BACKTRACK is perfect for me. NO I am NOT and Blackhat hacker. My only interest is converting my self taught computer skills into employable skills as a Network Admin or Penetration tester

---

