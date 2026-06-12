---
title: "USB Modem"
date: 2005-11-21
forum: Hardware &amp; Laptops
---

### Post by kenweill on 2005-11-21
hi..

im a new ubuntu linux user..

need some help regarding the installation of my modem connected to the USB port of my computer...

My Gilat Satellite Modem 360 is connected to the USB port of my computer. The modem was detected or displayed under the DEVICE MANAGER. But it doesn't seem to work. I cannot connect to the internet.

I need some ideas on how to connect to the internet regarding my situation.

---

### Post by sarah_b on 2005-11-21
[QUOTE=kenweill]
I need some ideas on how to connect to the internet regarding my situation.[/QUOTE]

In a terminal, type: sudo pppconfig
1. Then fill in the correct info for your ISP connection
2. Finish & write files, return to main menu
3. exit pppconfig utility
4. reboot computer
5. to start your connection
In a terminal, type: Sudo pon (name of Provider you entered in pppconfig)
6. to end your connection
In a terminal, type: Sudo poff (name of provider)

If pppconfig is not installed, use synaptic package manager.

Welcome to the forums kenweill......

---

### Post by kenweill on 2005-11-21
[QUOTE=sarah_b]In a terminal, type: sudo pppconfig
1. Then fill in the correct info for your ISP connection
2. Finish & write files, return to main menu
3. exit pppconfig utility
4. reboot computer
5. to start your connection
In a terminal, type: Sudo pon (name of Provider you entered in pppconfig)
6. to end your connection
In a terminal, type: Sudo poff (name of provider)

If pppconfig is not installed, use synaptic package manager.

[/QUOTE]

The procedure still don't work with my modem. I guess the procedure is for dial-up modem, or something like that. My connection is different. As long as the modem is turned on, its connected to the internet. I can use the modem in any computer using Windows XP. All i need is to install the driver for the modem and i can have an internet connection. But i can't do that in Linux(UBUNTU).

I contacted gilat networks but the drivers/software for their modem supports windows based OS only. They said that some of their clients are also using linux, and they successfully connect to the internet using windows emulator in order for their software to work. Although, I haven't tried it yet.

I switch between operating systems to connect to the internet. Windows during connecting to the internet. Linux during experimenting on how to connect to the internet.

---

### Post by sarah_b on 2005-11-21
kenweill, I totally missed that you had a satellite modem, sorry about that ! Maybe someone else will come along that can help you with that one.

---

### Post by kenweill on 2005-12-04
I have tried installing StarBlaze under wine and it pops up an error

Install Failed:
Installation fault - Require Windows 98 or higher.
Installation Requirements:
1.  Memory Ram: Win9x>=32mb, WinNT>=128mb
2. Not WinNT4, Not Win95.
3. IE Version 5 or above.
4.  Screen resolution 800X600 min. Screen colors 256 min
5. Free Space on Program Files drive
6. LAN or USB interface.


And another error on wine(console):

[root@workstation1-lazi-cec Modem Installer]# wine StarBlaze.exe
err:ntdll:NtQueryInformationToken Unhandled Token Information class 8!
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to 0x40
fixme:powermgnt:SetThreadExecutionState (0x80000001): stub, harmless.
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to (nil)
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to 0x40

fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to (nil)
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to 0x40
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to (nil)
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to 0x40
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to (nil)
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to 0x40
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to (nil)
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to 0x40
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to (nil)
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to 0x40
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to (nil)
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to 0x40
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to (nil)
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to 0x40
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to (nil)
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to 0x40
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to (nil)
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to 0x40
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to (nil)
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to 0x40
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to (nil)
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to 0x40
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to (nil)
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to 0x40
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to (nil)
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to 0x40
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to (nil)
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to 0x40
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to (nil)
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to 0x40
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to (nil)
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to 0x40
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to (nil)
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to 0x40
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to (nil)
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to 0x40
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to (nil)
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to 0x40
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to (nil)
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to 0x40
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to (nil)
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to 0x40
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to (nil)
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to 0x40
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to (nil)
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to 0x40
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to (nil)
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to (nil)
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to 0x80
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to 0x40
fixme:powermgnt:SetThreadExecutionState (0x80000000): stub, harmless.
fixme:powermgnt:SetThreadExecutionState (0x80000001): stub, harmless.
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to (nil)
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to 0x40
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to (nil)
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to 0x40
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to (nil)
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to 0x40
err:ntdll:NtQueryInformationToken Unhandled Token Information class 8!
fixme:msiexec:main Unknown parameter /D
fixme:msiexec:main Unknown function, ignoring
err:ntdll:NtQueryInformationToken Unhandled Token Information class 8!
Successfully registered dll L"C:\\windows\\system\\msi.dll"
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to (nil)
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to 0x40
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to (nil)
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to 0x40
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to (nil)
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to 0x40
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to (nil)
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to 0x40
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to (nil)
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to 0x40
fixme:powermgnt:SetThreadExecutionState (0x80000000): stub, harmless.
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to (nil)
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to 0x40
fixme:thread:NtSetInformationThread Set ThreadImpersonationToken handle to (nil)
fixme:msi:MsiInstallProductW L"c:\\Program Files\\Common Files\\Gilat\\0E151655_026E_40C0_8071_237DAB0ADE35.msi" L" REINSTALLMODE=vomus"
fixme:msi:MsiGetMode STUB (iRunMode=16)
err:msi:ACTION_ProcessUISequence Execution halted due to error (1627)
fixme:msi:ACTION_PerformUIAction UNHANDLED MSI ACTION L"Fatal_Error"

What can I do about this problem?
Or anyone have an idea?

---

### Post by mips on 2005-12-04
Who is your ISP ? Provide a link.
Where is the online manual for this beast ?

First I would suggest ditching the USB connection and connect via Ethernet Cable.

---

### Post by mips on 2005-12-04
From windows open a command prompt (dos window) and type **ipconfig /all** and post the complete output here.

---

### Post by kenweill on 2005-12-04
[QUOTE=mips]From windows open a command prompt (dos window) and type **ipconfig /all** and post the complete output here.[/QUOTE]

This is the output:

Windows IP Configuration



        Host Name . . . . . . . . . . . . : cec-server

        Primary Dns Suffix  . . . . . . . : 

        Node Type . . . . . . . . . . . . : Unknown

        IP Routing Enabled. . . . . . . . : No

        WINS Proxy Enabled. . . . . . . . : No



Ethernet adapter Local Area Connection:



        Connection-specific DNS Suffix  . : 

        Description . . . . . . . . . . . : Intel(R) PRO/100 VE Network Connection

        Physical Address. . . . . . . . . : 00-11-25-36-37-AE

        Dhcp Enabled. . . . . . . . . . . : No

        IP Address. . . . . . . . . . . . : 192.168.0.100

        Subnet Mask . . . . . . . . . . . : 255.255.255.0

        Default Gateway . . . . . . . . . : 



Ethernet adapter Gilat Satellite Modem 360:



        Connection-specific DNS Suffix  . : 

        Description . . . . . . . . . . . : Gilat USB Adapter

        Physical Address. . . . . . . . . : 00-A0-AC-00-82-EE

        Dhcp Enabled. . . . . . . . . . . : Yes

        Autoconfiguration Enabled . . . . : Yes

        IP Address. . . . . . . . . . . . : 203.189.15.44

        Subnet Mask . . . . . . . . . . . : 255.255.255.128

        Default Gateway . . . . . . . . . : 172.20.254.254

        DHCP Server . . . . . . . . . . . : 172.20.254.254

        DNS Servers . . . . . . . . . . . : 203.189.11.34

                                            203.189.11.35

                                            203.189.11.131

                                            203.189.11.132

        Lease Obtained. . . . . . . . . . : Sunday, December 04, 2005 11:15:39 PM

        Lease Expires . . . . . . . . . . : Sunday, December 04, 2005 11:45:39 PM

---

### Post by amconteh on 2005-12-04
Hello, i dont mean to cut into your topic but i am having almost the exact same problem that you are but i am using a cable modem instead of satellite. i went ahead and did the ipconfig /all thing and here is what i got. I hope you can get this to work until i can get a brand new computer with ethernet port this  new year. 

Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.


Windows IP Configuration

        Host Name . . . . . . . . . . . . : abass-2wzpr50jw
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . : insightbb.com
        Description . . . . . . . . . . . : ARRIS TOUCHSTONE DEVICE
        Physical Address. . . . . . . . . : 00-00-CA-44-BB-F2
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 12.202.229.109
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 12.202.229.1
        DHCP Server . . . . . . . . . . . : 12.223.2.34
        DNS Servers . . . . . . . . . . . : 63.240.76.135
                                            204.127.194.11
        Lease Obtained. . . . . . . . . . : Sunday, December 04, 2005 2:48:32 PM

        Lease Expires . . . . . . . . . . : Sunday, December 04, 2005 3:48:32 PM


:???:

---

### Post by mips on 2005-12-05
**kenweill**,

What is the ethernet card connected to ?
Who is your ISP Service provider ?

Try and configure you Ubuntu ethernet card for DHCP, you can add the DNS servers from the ipconfig /all output and let us know.

The Gilat 360 is also used in my country and the config only requires a basic DHCP setup via ethernet.

**amconteh**,
What brand * model cable modem do you use ?
Who is your cable/ISP, link please ?

---

### Post by kenweill on 2005-12-05
The Ethernet card(built-in) is connected to my workstations.

I have tried connecting the modem to the Ethernet but both, the computer and the modem, cannot detect each other. Even when the Ethernet is set to DHCP.

I have tried connecting the modem directly to the HUB, and the modem detected that it is connected to the pc(hub actually). But I don't think it would work in that setup. I don't know. 
I tried the setup. Modem to HUB. Then all the computers are connected to the HUB but, it doesn't work. I don't know. Its just my experiment. Crazy ideas.

---

### Post by mips on 2005-12-05
Give me a link to your ISP/Service providers website please.

---

### Post by amconteh on 2005-12-05
The link to my isp is [http://www.insightbb.com/](http://www.insightbb.com/) or  [http://www.insight-com.com/](http://www.insight-com.com/)  my  modem is  Arris Cable modem   model # CM450A P/N is TC00DA1450

---

### Post by mips on 2005-12-06
[QUOTE=amconteh]The link to my isp is [http://www.insightbb.com/](http://www.insightbb.com/) or  [http://www.insight-com.com/](http://www.insight-com.com/)  my  modem is  Arris Cable modem   model # CM450A P/N is TC00DA1450[/QUOTE]

I cant seem to find any usefull info on how to get the Linux and your USB Arris to work together. You might want to try PPPoE setup from the documentation Wiki.

My suggestion to you would be to buy an ethernet adapter for your PC, they are cheap and would make your life much easier. You might also require a router but if you have an ethernet port I doubt it.

---

### Post by mips on 2005-12-06
[QUOTE=kenweill]The Ethernet card(built-in) is connected to my workstations.

I have tried connecting the modem to the Ethernet but both, the computer and the modem, cannot detect each other. Even when the Ethernet is set to DHCP.

I have tried connecting the modem directly to the HUB, and the modem detected that it is connected to the pc(hub actually). But I don't think it would work in that setup. I don't know. 
I tried the setup. Modem to HUB. Then all the computers are connected to the HUB but, it doesn't work. I don't know. Its just my experiment. Crazy ideas.[/QUOTE]

Ok, lets try a different approach.

Connect your PC directly to the Gilat 360 via Ethernet.
Boot into MS Windows
Call your ISP and ask them to help you set up your PC to use the Ethernet connection. Do NOT once mention the word linux or ubuntu to them!!!
Tell them you dont want to install any special software on your PC. You just want it to work via the ethernet.
Once you have it working in windows post your ipconfig /all here again and we  will translate that to Ubuntu.

---

### Post by amconteh on 2005-12-06
Thanks a lot for trying Mips, i will just buy an ethernet card.

---

### Post by kenweill on 2005-12-09
[QUOTE=mips]Ok, lets try a different approach.

Connect your PC directly to the Gilat 360 via Ethernet.
Boot into MS Windows
Call your ISP and ask them to help you set up your PC to use the Ethernet connection. Do NOT once mention the word linux or ubuntu to them!!!
Tell them you dont want to install any special software on your PC. You just want it to work via the ethernet.
Once you have it working in windows post your ipconfig /all here again and we  will translate that to Ubuntu.[/QUOTE]

Windows IP Configuration



        Host Name . . . . . . . . . . . . : cec-server

        Primary Dns Suffix  . . . . . . . : 

        Node Type . . . . . . . . . . . . : Unknown

        IP Routing Enabled. . . . . . . . : Yes

        WINS Proxy Enabled. . . . . . . . : No



Ethernet adapter Local Area Connection:



        Connection-specific DNS Suffix  . : 

        Description . . . . . . . . . . . : Intel(R) PRO/100 VE Network Connection

        Physical Address. . . . . . . . . : 00-11-25-36-37-AE

        Dhcp Enabled. . . . . . . . . . . : Yes

        Autoconfiguration Enabled . . . . : Yes

        IP Address. . . . . . . . . . . . : 203.189.15.44

        Subnet Mask . . . . . . . . . . . : 255.255.255.128

        Default Gateway . . . . . . . . . : 172.20.254.254

        DHCP Server . . . . . . . . . . . : 172.20.254.254

        DNS Servers . . . . . . . . . . . : 203.189.11.34

                                            203.189.11.35

                                            203.189.11.131

                                            203.189.11.132

        Lease Obtained. . . . . . . . . . : Saturday, December 10, 2005 8:55:28 AM

        Lease Expires . . . . . . . . . . : Saturday, December 10, 2005 9:25:28 AM

This is the output of ipconfig /all.
But this is a different setup.
My modem cannot be detected when its connected directly to the NIC. This was detected in other connection.

Heres my setup now:

MODEM --> SWITCH(HUB) --> PC

As I said, it wont work from modem to PC. Cannot be detected.
Of course, It won't work as well if the accelerator/driver is not installed. Which is windows-based.

---

### Post by mips on 2005-12-10
The reason you can't connect directly from th PC to your Gilat360 is that you probably need a X-over cable but that is not required as going via the HUB is fine.

[B]What accelerator/Driver Software are you using, give me a link ???
Who is your ISP, give me a link ???[/B]

There should be no need for a driver when connecting to the Gilat via ethernet.

Fom Ubuntu:

Open System->Administration->Networking
Select the **Connections** tab:
Select your ethernet card and click properties.
Tick the Enable this connection box.
For configuration select DHCP

Select the **DNS** tab:
Add these 4 servers to the DNS servers list:
203.189.11.34
203.189.11.35
203.189.11.131
203.189.11.132

Click OK to close this window.

At the top right of your screen on the Gnome panelyou should have an Icon (two screens) for you network connection. Click on it and then click on the support tab. What information is displayed there ? Can you ping the gateway specified here ? Can you ping one of the dns servers listed above ?

Also show output for these commands:
sudo mii-tool eth0
ifconfig eth0
route -n

Can you ping the default gateway ? 
Can you ping one of the dns servers listed above ?

---

### Post by kenweill on 2005-12-10
No.
I cannot ping the Gateway nor the DNS server.
Request timed out.

I have tried installing UBUNTU 5.10(coz i reformat my hard drive b4), there's this error on DHCP.

No Default Route Was Set

I don't know what that mean.
I tried to configure manually with the IP address, gateway and dns but still i got an error.

Gateway unreachable

Or someting like that. So i did not continue the setup/installation.

My ISPs address is [http://www.azcomfinance.com](http://www.azcomfinance.com)
The accelerator/driver can be found at [ftp://ftp.mozcom.com/pub/starblaze](ftp://ftp.mozcom.com/pub/starblaze)

---

### Post by kenweill on 2005-12-10
I have contacted my ISP [email]magsajo@yahoo.com[/email] regarding the connection i made.
I also asked them if it works using a router.

He replied:

> 
As I've said before, the modem needs an
accelerator/driver software to run. This is a
Window-based software and it can only run on Windows
environment.  Unless you can install Windows operating
system on your router, then the modem will work when
connected to a router.  But I don't think there are
any routers capable of that.

If you connected the modem directly to the NIC, then
your PC will not really detect the modem, but rather,
it will detect the NIC that is installed to your PC.
If the NIC is working fine, then the modem must be
working fine also. But you still have to install the
StarBlaze to act as the accelerator of the modem.

The modem will only be detected by Windows if you
connect it via USB port.

The basic setup should be --- Outdoor unit (satellite
dish) connected to the modem via RF-IN(Receive) and
RF-OUT(Transmit) terminals, and then the modem is
connected to a server PC via USB or LAN port, and the
software StarBlaze is installed on the server PC.


---

### Post by mips on 2005-12-10
I will look at the links you provided and come back to you later.

The technology implementation must be different in some way seeing software is required. Where I live we have the exact same Gilat360 and no drivers or additional software is required.

I will see what I can figure out.

---

### Post by kenweill on 2005-12-12
[QUOTE=mips]I will look at the links you provided and come back to you later.

The technology implementation must be different in some way seeing software is required. Where I live we have the exact same Gilat360 and no drivers or additional software is required.

I will see what I can figure out.[/QUOTE]

Mips,

Aside from the IP address that was produced by ipconfig /all, there are two ip address that is not included with that command.

The accelerators, Internet Page Accelerator(IPA) and Internet over  Satellite Accelerator(IoSA), also connects to another IP address.

Heres the info:

Accelerators:
   Internet over Satellite Accelerator:
     Primary Server IP Address     172.21.1.10
 
   Internet Page Accelerator:
     Server IP Address                192.168.30.10
     Server Port                         9876
     NMS Server IP Address          0.0.0.0
     NMS Server Port                   0
     RPA Port                             9877

I guess thats the problem. I don't know how that works. I don't know what to do under linux.

---

### Post by kenweill on 2005-12-29
Attached is my Modem Technical Specs.

Its from a PDF file but I just did copy it to jpeg. Can't upload large PDF file.

---

### Post by elfgoh on 2005-12-31
Hi, I a newbie too. I manageed to setup up USB Aztech diaup modem using some packages from this website. You may want to give it a try.

[http://linmodems.technion.ac.il/](http://linmodems.technion.ac.il/)



Cheers!

---

### Post by kenweill on 2006-01-01
[QUOTE=elfgoh]Hi, I a newbie too. I manageed to setup up USB Aztech diaup modem using some packages from this website. You may want to give it a try.

[http://linmodems.technion.ac.il/](http://linmodems.technion.ac.il/)

Cheers![/QUOTE]

I have asked for help in linmodems but the modem they support are the one that is connected to the phone line.

I have a Broadband modem through satellite communications. (xDSL over satellite communications). They have xDSL over phone line.

Thats the problem.

---

