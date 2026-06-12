---
title: "dell perc 5/i - megaraid storage manager"
date: 2008-05-04
forum: Hardware
---

### Post by leondo on 2008-05-04
Has anyone managed to install megaraid storage manager (it's a monitoring tool from lsi logic for their raid controllers) to ubuntu(any version)?

I have a dell perc 5/i (ubuntu 8.04) and I'm trying to install MegaCli and MegaRaid Storage Manager. MegaCli comes with rpm format, which I converted to deb using alien and installed successfully.

Now I'm trying to install MegaRaid Storage Manager which comes in a tar.gz. It contains a bunch of scripts and a bunch of rpms. Here is a ls :
deleteOldVersion.sh readme.txt
install.sh RunRPM.sh
libstdc++34-3.4.0-1.i386.rpm sas_ir_snmp-3.13-0005.i386.rpm
LSI-AdapterSASIR.mib sas_snmp-3.13-0004.i386.rpm
LSI-AdapterSAS.mib ServerInstall.sh
MegaRAID_Storage_Manager-2.35-01.noarch.rpm

I converted MegaRAID_Storage_Manager-2.35-01.noarch.rpm, sas_ir_snmp-3.13-0005.i386.rpm, sas_snmp-3.13-0004.i386.rpm successfully using alien, but I can't convert libstdc++34-3.4.0-1.i386.rpm successfully.
Any ideas??

---

### Post by leondo on 2008-05-04
Anyone?

---

### Post by honeydew on 2008-05-07
Sorry I cant help with this, however maybe you can help me.. I am purchasing a handful of Dell 2950 series servers.  They come with the perc 5/i or perc 6/i raid controller.  After searching around the forums I have found a few instances of people saying they had a bit of trouble getting things working out of the box(this is ubuntu 6.06)

reference:
[http://ubuntuforums.org/showthread.php?t=226114](http://ubuntuforums.org/showthread.php?t=226114)
[http://ubuntuforums.org/showthread.php?t=226114&page=3](http://ubuntuforums.org/showthread.php?t=226114&page=3)

granted this was for a older version of ubuntu, and I will be installing 8.04 on these servers.. can you shed a bit more light on your current experience?

---

### Post by honeydew on 2008-05-07
btw.. libstdc is in the repositories.. if you install via apt-get/synaptic you should be able to point mega raid in the right direction during compilation 

$ aptitude search stdc
p   lib64stdc++6                                                            - The GNU Standard C++ Library v3 (64bit)                                          
p   lib64stdc++6-4.1-dbg                                                    - The GNU Standard C++ Library v3 (debugging files)                                
p   lib64stdc++6-4.2-dbg                                                    - The GNU Standard C++ Library v3 (debugging files)                                
v   libstdc++-dev                                                           -                                                                                  
i   libstdc++5                                                              - The GNU Standard C++ Library v3                                                  
p   libstdc++5-3.3-dbg                                                      - The GNU Standard C++ Library v3 (debugging files)                                
p   libstdc++5-3.3-dev                                                      - The GNU Standard C++ Library v3 (development files)                              
p   libstdc++5-3.3-doc                                                      - The GNU Standard C++ Library v3 (documentation files)                            
p   libstdc++5-3.3-pic                                                      - The GNU Standard C++ Library v3 (shared library subset kit)                      
i   libstdc++6                                                              - The GNU Standard C++ Library v3                                                  
p   libstdc++6-4.1-dbg                                                      - The GNU Standard C++ Library v3 (debugging files)                                
p   libstdc++6-4.1-dev                                                      - The GNU Standard C++ Library v3 (development files)                              
p   libstdc++6-4.1-doc                                                      - The GNU Standard C++ Library v3 (documentation files)                            
p   libstdc++6-4.1-pic                                                      - The GNU Standard C++ Library v3 (shared library subset kit)                      
p   libstdc++6-4.2-dbg                                                      - The GNU Standard C++ Library v3 (debugging files)                                
i A libstdc++6-4.2-dev                                                      - The GNU Standard C++ Library v3 (development files)                              
p   libstdc++6-4.2-doc                                                      - The GNU Standard C++ Library v3 (documentation files)                            
p   libstdc++6-4.2-pic                                                      - The GNU Standard C++ Library v3 (shared library subset kit)                      
p   libstdc++6-dbg                                                          - The GNU Standard C++ Library v3 (debugging files)                                
p   libstdc++6-dev                                                          - The GNU Standard C++ Library v3 (development files)                              
p   libstdc++6-doc                                                          - The GNU Standard C++ Library v3 (documentation files)                            
p   libstdc++6-pic                                                          - The GNU Standard C++ Library v3 (shared library subset kit)

---

### Post by leondo on 2008-05-07
Yes of course I can help you..
Basically I don't have a dell server(2950 etc). I only have dell perc 5/i integrated controller. I purchased it so I can build my own nas server. I installed 8.04 server edition on my box. The card is properly recognized out of the box by the operating system(ubuntu), with the megaraid driver.

The problem is that I want to find a way to monitor the card, so I can do further operations(check consistency, patrol read, rebuild array, etc..). There are 4 options I found so far for monitoring the card, which are :

1)MegaCli : Command-line utility provided by Lsi Logic. I managed to convert the rpm that Lsi provides from their website to deb using alien and installed it successfully. However I didn't manage to make MegaCli see my card. I'm working on that..

2)MegaRAID Storage Manager: Application with gui provided by Lsi Logic. I didn't manage to install this succefully on ubuntu 8.04

3)Omsa: Monitoring tools from Dell for their servers. I installed these from some instructions I found on linux.dell.com, but it didn't helped me much

4)Megactl: Is an open source project for lsi's cards, similar to MegaCli, but with fewer options. I installed this successfully and I made it recognize my card. It works so far

But because I don't feel that comfortable with megactl(which the only I managed to work properly), I installed winxp on another partition just for the monitoring tools(MegaRAID Storage Manager)

Hope that helps :)


I installed both libstdc++6 and 5, but it didn't help

---

### Post by jnusa on 2008-09-15
Hi
I'm looking into buying a Dell Perc 5/i controller for nas, and I was wondering if the controller supports spindown (and maybe staggered spindown?), where the raid is powered off when inactive? I see, you have trouble controlling the controller from the OS - However I assume that BIOS setup is still possible with the unit?! Thanks in advance.

---

### Post by limaxray on 2008-12-08
So I just figured out how to get MegaRAID storage manager running on Hardy and it seems to work fairly well, so I figured I'd share what I did.

First, convert MegaRAID storage manager RPM to a deb package using alien. Make sure you include the script switch like so:

sudo apt-get install alien  (if you don't already have it)
sudo alien --script MegaRAID_Storage_Manager-2.35-01.noarch.rpm 

Next, install the resulting deb package using your preferred method.

sudo dpkg -i megaraid-storage-manager_2.35-2_all.deb

Next, you're going to need to edit the UI startup script, but first make it editable:

sudo chmod 755 /usr/local/MegaRAID Storage Manager/startupui.sh

You're going to need to edit it for two things: first you need to add a line to change to the MSM directory, and second you need to change the jre directory to call the system's currently (or not yet) installed jre.  Your startup script should look like this:

```
. /etc/init.d/msm_profile
cd "/usr/local/MegaRAID Storage Manager/"
/usr/bin/java -Duser.country=US -Duser.language=en -classpath .:GUI.jar:monitorgui.jar:DebugLog.jar GUI.VivaldiStartupDialog ajsgyqkj=71244
```

Next you need to grab a proper jre as the jre included with MSM doesn't work on Hardy.

apt-get install sun-java6-jre

Finally, run the startupui.sh script and it should work.

If you get errors in the terminal about not being able to connect to your address, you'll need to start a couple daemons like so:

sudo /etc/init.d/vivaldiframeworkd start
sudo /etc/init.d/mrmonitor start

Also, I almost forgot to mention - In order to login, you'll need to enable root access.  This is kind of a pain and doesn't make me terribly happy, but I haven't yet figured out how to enable other users to connect with full permissions.

Hope this helps anyone else who needs it.

---

### Post by fadetoblack82 on 2009-03-09
hey guys, sorry i cant really contribute to the OPs question, but i had some questions regarding perc 5i. i posted it here:
[http://ubuntuforums.org/showthread.php?t=1091758&highlight=perc](http://ubuntuforums.org/showthread.php?t=1091758&highlight=perc)

also, i spent about 3 hours trying to get dell's omsa working but was not able to get it working. i am running ubuntu 9.04 alpha 5. could it be because maybe my motherboard doesn't support IPMI? chipset is nforce 730i.

---

### Post by cimboo on 2009-10-05
Hey,

it was possible for me to install the msm. But I have a problem to start it. Can someone help me with the starting script?

```
root@Horst:~/MSM/disk# /etc/init.d/vivaldiframeworkd start
/etc/init.d/vivaldiframeworkd: 18: Syntax error: Bad for loop variable
```here my insallation instructions:

```
wget http://www.lsi.com/DistributionSystem/AssetDocument/2.91-03_Linux_MSM.zip

aptitude install unzip

aptitude install alien

aptitude (libstdc++6-4.3-dev installieren)

unzip 2.91-03_Linux_MSM.zip

cd MSM/

tar -xzvf MSM_linux_installer-2.91-03.tar.gz

cd disk/

alien --script MegaRAID_Storage_Manager-2.91-03.noarch.rpm

dpkg -i megaraid-storage-manager_2.91-4_all.deb

update-rc.d vivaldiframeworkd defaults

update-rc.d mrmonitor defaults
```
here you can see the /etc/init.d/vivaldiframeworkd:

```

#!/bin/sh
#description: Framework serice startup/shutdown script

#Function to check status of Framework service
check_status() {
x=`ps -ef|grep java|grep Framework.jar`
if [ "$x" = "" ] ; then
        return 3;
fi
return 0
}

#Function to start Framework service
start() {
\rm -f /tmp/network_present
. /etc/init.d/msm_profile
network_flag=0
for (( i=0; i < 20; i++ ))
do
if [ -f "$MSM_HOME/Framework/TestNetworkCapability.class" ]
then
echo "$MSM_PRODUCT with Network Capability">>/dev/null
"$MSM_HOME/jre/bin/java" -classpath "$MSM_HOME/jre/lib/rt.jar:$MSM_HOME/Framework" TestNetworkCapability
if [ -f /tmp/network_present ]
then
network_flag=1
i=21
\rm -f /tmp/network_present
else
sleep 5
fi
else
echo "$MSM_PRODUCT without Network Capability">>/dev/null
network_flag=1
i=21
fi
done
if [ $network_flag -eq 1 ]
then
echo "Trying to start Framework.....">>/dev/null
else
echo "$MSM_PRODUCT failed to start Framework..... Check your Network">>/dev/null
echo "Trying to start Framework without Network Capability.....">>/dev/null
fi
sh "$MSM_HOME/Framework/startup.sh" >> /dev/null 2>>/dev/null &
}

#function to stop Framework Service
stop() {
. /etc/init.d/msm_profile
sh "$MSM_HOME/Framework/shutdown.sh" >> /dev/null &
}

case "$1" in
        start)
                check_status
                status=$?
                if [ $status = 0 ]; then
                        echo "Framework is already running....."
                else
                        echo "Starting Framework: "
                        start
                fi
                ;;
        stop)
                check_status
                status=$?
                if [ $status = 3 ]; then
                        echo "Framework is already stopped....."
                else
                        echo "Shutting down Framework: "
                        stop
                fi
                ;;
        restart|reload)
                $0 stop
                sleep 20
                $0 start
                ;;
        status)
                check_status
                RETVAL=$?
                if [ $RETVAL = 0 ]; then
                        echo "Framework is running..."
                else
                        if [ $RETVAL = 3 ]; then
                                echo "Framework is stopped..."
                        else
                                echo "Framework status unknown..."
                        fi
                fi
                ;;
        *)
                echo "Usage: $0 {start|stop|restart|status}"
                exit 1
esac
exit $RETVAL

```

---

### Post by fadetoblack82 on 2009-10-05
try this:

backup your /etc/init.d/vivaldiframeworkd script first. then edit it as root and replace line 18:

```
for (( i=0; i < 20; i++ ))
```

with this:

```
for i in `seq 0 19`
```

that should get around the bad for loop variable error. i think the error is because /bin/sh is actually dash

---

### Post by cimboo on 2009-10-07
thank you, the loop error is gone. but the script does not start the monitor. i should install opensuse to use this program...

---

### Post by Allan Tung on 2009-10-19
Hello,
 
I manage to install the Megaraid Storage Manager but it cannot start the application. The terminal screenshot is attached with this message. Hopefully someone know the reason. 
 
Thanks.

---

### Post by bijur on 2009-12-12
So... I think I've made some progress with the installation of the MegaRAID Storage Manager.

But I was getting an error when loading the framework dependencies.

I've discovered that the problem resides in the two libraries that are native, and are used in the Java environment through JNI (Java Native Interface).

Apparently, without those two libraries, the framework doesn't load, and the graphical interface can't "see" the server with the PERC/6i board.

I'm running Ubuntu 8.04 on a Dell Server with the PERC/6i RAID Controller.

If anyone know how to solve this... 

Best for all.

Cheers.

---

### Post by Laykun on 2009-12-19
Yes, a fix for this would be great as I'm trying to use the interface for my Dell Perc 5/i but it wont load the framework module.

---

### Post by Laykun on 2009-12-20
> **Laykun said:**
> Yes, a fix for this would be great as I'm trying to use the interface for my Dell Perc 5/i but it wont load the framework module.

Ok, I managed to fix this on my system with karmic 64bit. The problem I was having was mrmonitor wasn't starting due to an error with libstdc++5, as in it did not exist. libstdc++5 isn't available for karmic so I downloaded the packages for jaunty and manually installed them. [http://packages.ubuntu.com/jaunty/libstdc++5](http://packages.ubuntu.com/jaunty/libstdc++5). You'll need the 32bit version to run the framework.

---

### Post by bijur on 2010-02-08
So many thanks! It worked like a charm!

BTW, it works also for the Dell PERC 6/i!
Thanks guys!

---

### Post by BooDaddy on 2010-03-06
I am having problems  gettting my Storage Manager installed so I can manage my PERC 5i card.
I am running Ubuntu Server 9.10 and I have followed the directions in this entire thread.

I am able to start Vivaldi and mrmonitor without any errors, but I cant get storage manager to connect (which I am running from another PC) to the server with the perc card.

I had even more problems trying to start the startupui.sh as it gives an error trying to locate JRE. 

Any suggestions?

---

### Post by EvilGenius007 on 2010-03-10
I'm also having trouble monitoring a PERC 5/i with 9.10, but I happen to be running the 64-bit desktop variety.

What I've done so far (to best of my recollection and understanding):

1. Download & save MegaCLI for Linux from [LSI's website]("http://www.lsi.com/obsolete/megaraid_sas_8480e.html") (the Support & Downloads tab for the 8480e product, with the "Current" radio button selected).
2. Convert and install the .rpm using the following console commands:
[FONT=Fixedsys]sudo apt-get install alien
sudo alien --to-tgz  MegaCli-1.01.39-0.i386.rpm
sudo tar xvfz MegaCli-1.01.39.tgz
sudo cp MegaCli64 /usr/sbin/MegaCli[/FONT]
3. Find out that while the "MegaCli" command now produces output, it also doesn't recognize my controller. Specifically, the command:
[FONT=Fixedsys]MegaCli -AdpCount[/FONT]
produces the output
[FONT=Fixedsys]Controller Count: 0.[/FONT]
4. From the instructions in this thread: Download & save MegaRAID Storage Manager for Linux from [URL="http://www.lsi.com/obsolete/megaraid_sas_8480e.html"]LSI's website
[/URL] 5. Use the GUI Archive Manager to unpackage the MSM_linux_install-2.35-01.tar.gz file, creating a directory called "disk" which contains "MegaRAID_Storage_Manager-2.35-01.noarch.rpm"
6. Install it with the following instructions:
[FONT=Fixedsys]sudo alien --script MegaRAID_Storage_Manager-2.35-01.noarch.rpm 
sudo dpkg -i megaraid-storage-manager_2.35-2_all.deb[/FONT]
[FONT=Verdana]7. Modify the startup script as follows:[/FONT]
[FONT=Fixedsys]sudo chmod 755 /usr/local/MegaRAID\ Storage\ Manager/startupui.sh
sudo nano /usr/local/MegaRAID\ Storage\ Manager/startupui.sh[/FONT]
changing the contents to:
```
. /etc/init.d/msm_profile
cd "/usr/local/MegaRAID Storage Manager/"
/usr/bin/java -Duser.country=US -Duser.language=en -classpath .:GUI.jar:monitorgui.jar:DebugLog.jar GUI.VivaldiStartupDialog ajsgyqkj=71244
```8. Install the suggested version of java:
[FONT=Fixedsys]sudo apt-get install sun-java6-jre
[FONT=Verdana]9. Run the startup script:
[FONT=Fixedsys]cd /usr/local/MegaRAID\ Storage\ Manager/
./startupui.sh[/FONT]
10. Discover that it didn't report my controller either
11. Downloaded the amd64 file from one of the mirrors at [/FONT][/FONT][http://packages.ubuntu.com/jaunty/libstdc++5](http://packages.ubuntu.com/jaunty/libstdc++5) and installed with the GDebi Package Installer (default)
12. Re-ran startupui.sh and found it still didn't report my controller
13. Came here to ask for help!

HELP!!

I will note that one step I didn't attempt & don't understand is giving root access to ... something!? in order to "login" with the MegaRAID Storage Manager. > **limaxray said:**
> Also, I almost forgot to mention - In order to login, you'll need to enable root access.

I should also note, my reason for wanting these tools is to expand my existing, functional RAID 5 array from 4 drives to 5. I have no issues with Ubuntu recognizing, mounting, and making the space from the existing array available, and I have confirmed in the "BIOS" of the card that the 5th drive is connected and operational.

---

### Post by BooDaddy on 2010-03-22
Im still having problems with this.

Is there a solution that would run the megaraid manager as a daemon (maybe MegaRAID CLI) and then I can connect to my ubuntu 9.10 box that has the PERC card from another winxp box that is running the megaraid java client?

When I boot my ubuntu box into windowsXP (which is the only way to manage my raid right now) I am able to connect to  the megaraid client from another PC.

Will the MegaRAID CLI have an option to run at boot an allow connections from other PCs running the java megaraid client?

---

### Post by ArNike on 2010-04-05
I have problems with it too. But my case is slightly different. When I launch 'vivaldiframeworkd' it goes with the following error:
MSM Framework version 2.12
Loaded Plugin:: Log Service Plugin version: 1.03
Loaded Plugin:: Authenticate Plugin version: 1.01  Native library: 1.02

Before calling storelibexit..cmd = SL_EXIT_LIB

After calling storelibexit..return = 1
IR PluginCallBack Thread shutdown called ...
Sender will send port: 49258
Loaded Plugin:: NetworkCapability Plugin version: 1.09
Loaded Plugin:: CIM Plugin version :1.04
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00000000, pid=3399, tid=3072261008
#
# JRE version: 6.0_19-b04
# Java VM: Java HotSpot(TM) Server VM (16.2-b04 mixed mode linux-x86 )
# Problematic frame:
# C  0x00000000
#
# An error report file with more information is saved as:
# /usr/local/MegaRAID Storage Manager/Framework/hs_err_pid3399.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#
./startup.sh: line 5:  3399 Aborted   /usr/lib/java/bin/java -classpath ../jre/lib/rt.jar:../jre/lib/jsse.jar:../jre/lib/jce.jar -Djava.library.path=. -jar Framework.jar

In hs_err_pid3399.log file I can make out absolutely nothing. There is just a bunch of hex codes and other rubbish there. So, I'm not posting it here.

BooDaddy, you're partially right, but I don't think that MegaRAID CLI will do here simply because CLI can't work as a daemon by definition :-)
I want to install MSM with that thought in mind, that I will be able to connect to MSM server from another host with MSM client installed in order to remotely manage RAID.
But so far, with no success.

---

### Post by JD82 on 2010-11-05
[CENTER][SIZE="6"]**YAY!**[/SIZE] :mrgreen:

[[img]http://www.anddev.it/adipic/thumbs/msmonubuntu.png[/img]](http://www.anddev.it/adipic/images/msmonubuntu.png)[/CENTER]

**[SIZE="5"]How to install MegaRAID Storage Manager 8.10-04 on Ubuntu 10.10[/SIZE]**
[SIZE="3"]
[LIST=1]
[*]Download and install [_megacli_5.00.12-1_i386.deb_]("http://hwraid.le-vert.net/ubuntu/pool-lucid/megacli_5.00.12-1_i386.deb") ([_mirror_]("http://www.megaupload.com/?d=WVALPMLG")) or [_megacli_5.00.12-1_amd64.deb_]("http://hwraid.le-vert.net/ubuntu/pool-lucid/megacli_5.00.12-1_amd64.deb") ([_mirror_]("http://www.megaupload.com/?d=11EAX8MY"))
[*]Download and install [_megaraid-storage-manager_8.10-04_i386.deb_]("https://launchpad.net/~ast/+archive/test7/+build/1977823/+files/megaraid-storage-manager_8.10-04_i386.deb") ([_mirror_]("http://www.megaupload.com/?d=HDVFO64M")) or [_megaraid-storage-manager_8.10-04_amd64.deb_]("https://launchpad.net/~ast/+archive/test7/+build/1977822/+files/megaraid-storage-manager_8.10-04_amd64.deb") ([_mirror_]("http://www.megaupload.com/?d=XHEDA4LL"))
[*]Set a password for the root user:
```
sudo passwd
```
[*]Start MSM and login as root!
```
/usr/local/MegaRAID\ Storage\ Manager/startupui.sh
```
[/LIST][/SIZE]

**[SIZE="4"]Launcher settings (optional)[/SIZE]**
[SIZE="3"]```
Exec="/usr/local/MegaRAID Storage Manager/startupui.sh"
Name=MegaRAID Storage Manager StartupUI
Icon=/usr/local/MegaRAID Storage Manager/setdisp.png
```[/SIZE]

---

### Post by BooDaddy on 2010-11-05
Holy crap! You sir, are awesome! I will try this out this weekend and report my results!
Thanks!

---

### Post by BooDaddy on 2010-11-08
Well... mixed results.  I was able to get everything installed, and the GUI even launches.  But it does not find my server. I have tried having it goto 127.0.0.1 but no luck.  It still will not pickup my SAS card.

Any suggestions?  I have tries running the MSM as root and everything.

---

### Post by sunnynice on 2010-11-09
> **BooDaddy said:**
> Well... mixed results. I was able to get everything installed, and the GUI even launches. But it does not find my server. I have tried having it goto 127.0.0.1 but no luck. It still will not pickup my SAS card.
 
Any suggestions? I have tries running the MSM as root and everything.
 sounds hard prob to deal with.

---

### Post by JD82 on 2010-11-10
> **BooDaddy said:**
> Well... mixed results.  I was able to get everything installed, and the GUI even launches.  But it does not find my server. I have tried having it goto 127.0.0.1 but no luck.  It still will not pickup my SAS card.

Any suggestions?  I have tries running the MSM as root and everything.

Are you using amd64 architecture? I did some testing and actually does not seem to find any server on amd64 :(.

---

### Post by BooDaddy on 2010-11-10
Yes, I am indeed running 64 bit. Oh well. Was so close :) Maybe someone will get this working on 64 bit, as thats a bit above my knowledge level :(

---

### Post by BooDaddy on 2011-01-24
Well,
I just tried this on another machine I built.  This time I am using Ubuntu Server 10.10 32 bit. I have ubuntu-desktop installed, and followed the directions that JD82 posted.

MSM launches, but it never is able to connect to the card.  I have tried 127.0.0.1 as the host and still doesnt find it.  Any suggestions?

What other packages could you suggest JD82?

---

### Post by maxim99 on 2011-01-25
I just wanted to add my little bit in here. I noticed that after applying several fixes referenced in this thread, the /etc/init.d/mrmonitor was still not functioning properly. I found that this was due to the lack of a 32-bit comparability library on my system.

I found that there is no such library in debian/ubuntu so I did the next best thing. I search around for the libstdc++5 package to install on my system.

I found it here: [http://packages.ubuntu.com/maverick/i386/libstdc++5/download](http://packages.ubuntu.com/maverick/i386/libstdc++5/download)

And installed it via the command:
```
dpkg --force-architecture libstdc++5_3.3.6-20_i386.deb
```

Previously mrmonitor was providing an error about libstdc++.5.so and saying No such file or directory.

A symlink to the .6.so didn't work out so I installed the 32bit version of .5.so and the error message no longer appears.

I'm now having difficulties getting the client software to see the server like most others in this thread.

---

### Post by maxim99 on 2011-01-26
I was able to get it to work. However, I ended up using Intel's RAID Web Console 2.

I found that the key to getting it to work is setting up the libraries so that they're functioning.

For me the key library was libxerces-c.so.28. This library came along with Intel RAID Web Console 2 in a separate RPM in an apache directory.

I symlinked the library into my /usr/lib and then did ldconfig, restarted the services and afterwards the controller was listed.
```
# ln -s /opt/lsi/Apache/libxerces-c.so.28 /usr/lib/libxerces-c.so.28
# ldconfig
```
```
# ldd /usr/local/bin/mrmonitord
        linux-gate.so.1 =>  (0xf771a000)
        libdl.so.2 => /lib32/libdl.so.2 (0xf76fa000)
        librt.so.1 => /lib32/librt.so.1 (0xf76f1000)
        libpthread.so.0 => /lib32/libpthread.so.0 (0xf76d7000)
        libxerces-c.so.28 => /usr/lib/libxerces-c.so.28 (0xf72c8000)
        libstdc++.so.6 => /usr/lib32/libstdc++.so.6 (0xf71d2000)
        libm.so.6 => /lib32/libm.so.6 (0xf71ac000)
        libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf718d000)
        libc.so.6 => /lib32/libc.so.6 (0xf7032000)
        /lib/ld-linux.so.2 (0xf771b000)
```

---

### Post by iikoo on 2011-03-09
Damn, not working in 10.10 maveric 64bit. Have you figured this out yet? Seems to be the same as with everyone else, no server found. Vivaldiframework does start, and mrmonitor tries to, but according to syslog it does not find my controller!

---

### Post by xchema on 2011-03-31
Maybe this can help:
[http://kb.lsi.com/KnowledgebaseArticle16108.aspx](http://kb.lsi.com/KnowledgebaseArticle16108.aspx)

---

### Post by kami^_^ on 2011-05-14
Maybe it helps someone.

> **xchema said:**
> Maybe this can help:
[http://kb.lsi.com/KnowledgebaseArticle16108.aspx](http://kb.lsi.com/KnowledgebaseArticle16108.aspx)

It works,  but MSM can't find server on loopback (127.0.0.1)  
MSM CAN find server only on external IP.
After setting password for root i can login from another machine (windows).
Under Linux i can login but MSM shows nothing except rotating circle. 

(Ubuntu 11.04 x64)

---

### Post by notanatheist on 2011-05-31
3Ware FTW any day of the week. LSI sucks so hard. It is sad they acquired 3Ware and Intel uses them for their controllers too. All the tools are RPM and in many cases not x64. Get with it LSI. 

At least Adaptec's software usually installs and works with minimal fuss. They just suck at updating FW for their cards. Would a 3Ware dev kindly step forward and smack the LSI team around to improve their software?!

Argh!

</rant>

---

### Post by zhouz on 2011-06-14
After much fiddling I was able to install the Megaraid Storage Manager on a clean install of 10.04.2 x64 server. This worked for me to be able to monitor the Intel SASUC8I cards in a couple of my servers which run on LSI 1068e. I'm sure this will work for monitoring other cards like the dell perc

```
#installing MSM on ubuntu 10.4.2 x64 server LTS
#you should enable universe repo before starting
#also, must enable root account to connect from gui
sudo passwd
mkdir msm
cd msm
sudo apt-get update
sudo apt-get install libc6-i386 lib32gcc1 lib32z1 lib32stdc++6 ia32-libs lib32icu42
wget http://mirrors.kernel.org/ubuntu/pool/universe/g/gcc-3.3/libstdc++5_3.3.6-21ubuntu1_amd64.deb
sudo dpkg -i libstdc++5_3.3.6-21ubuntu1_amd64.deb
wget http://mirrors.kernel.org/ubuntu/pool/universe/g/gcc-3.3/libstdc++5_3.3.6-21ubuntu1_i386.deb
dpkg-deb -x libstdc++5_3.3.6-21ubuntu1_i386.deb lib32stdc++5
sudo cp ./lib32stdc++5/usr/lib/libstdc++.so.5.0.7 /usr/lib32
sudo ln -s /usr/lib32/libstdc++.so.5.0.7 /usr/lib32/libstdc++.so.5
wget http://mirrors.kernel.org/ubuntu/pool/universe/x/xerces-c2/libxerces-c28_2.8.0+deb1-2build1_i386.deb
dpkg-deb -x libxerces-c28_2.8.0+deb1-2build1_i386.deb lib32xerces-c28
sudo mkdir -p /opt/lsi/Apache/
sudo cp ./lib32xerces-c28/usr/lib/libxerces-c.so.28.0 /opt/lsi/Apache/
sudo ln -s /opt/lsi/Apache/libxerces-c.so.28.0 /opt/lsi/Apache/libxerces-c.so.28
sudo ln -s /opt/lsi/Apache/libxerces-c.so.28 /usr/lib/libxerces-c.so.28
sudo ldconfig
wget https://launchpad.net/~ast/+archive/test7/+build/1977822/+files/megaraid-storage-manager_8.10-04_amd64.deb
sudo dpkg -i megaraid-storage-manager_8.10-04_amd64.deb
```

I was then able to connect to the server from a windows install of MSM (the one I used is at [http://www.lsi.com/DistributionSystem/User/AssetMgr.aspx?asset=56650](http://www.lsi.com/DistributionSystem/User/AssetMgr.aspx?asset=56650) )

---

### Post by andreas.kotowicz on 2012-03-12
see this posting for up-to-date instructions:

[https://plus.google.com/u/0/107102143611228129256/posts/Teoy9HoCNUx]("https://plus.google.com/u/0/107102143611228129256/posts/Teoy9HoCNUx")

---

