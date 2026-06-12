---
title: "firestarter disabled yahoo messenger"
date: 2005-11-04
forum: General Help
---

### Post by kroiz on 2005-11-04
Hi,
Since I installed firestarter. I am not able to connect to yahoo using gaim. Even that Firestarter is closed most of the time (I only use firestarter once in a while to share internet connection with my old pc).

is it possible that firestarter closed some previously opened ports?
is there a way to connect to yahoo when my firestarter is closed?

thanks.

---

### Post by kroiz on 2005-11-04
how can I see which ports are open and which are closed?
and why is it that when I shutdown ubuntu It says something about shuting down firestarter even though firestarter was not run?

---

### Post by SlowJet on 2005-11-04
When you install Firestarter is sets itself up as the iptables and loads at bootup.
You need to configure the setting with the GUI.
But if you never did the firewall is stll runiing.

You need to open the ports needed by YM, which I would think are the same for any chat / messager program.

Depending on how many function of the messager you what to use determines which ports to open.

In Firestarter gui you should also set the prefernces as well as the sevices and then individual ports (which may automaitacally id a sevice when the port number is typed in.

Once all the normal services are setup you click on apply button, close the gui and the firewall is working as needed.

SJ

---

### Post by kroiz on 2005-11-05
[QUOTE=SlowJet]When you install Firestarter is sets itself up as the iptables and loads at bootup.
You need to configure the setting with the GUI.
But if you never did the firewall is stll runiing.[/QUOTE]
I dont see its icon in the top panel nor do I see its name in the system-monitor. or ps -elf|grep -i firestarter

[QUOTE=SlowJet]You need to open the ports needed by YM, which I would think are the same for any chat / messager program.

Depending on how many function of the messager you what to use determines which ports to open.[/QUOTE]

I tried running firestarter and added rules for ports 20,23,25,80,119,5000-5050
but to no avail.
btw I dont know if it helps you help me but ICQ and MSN do connect.

also I read on the internet that Yahoo also uses port 80, is it possible? 
I thought that port 80 is used for internet. so wont the browsers will get what ever yahoo sends on that port and vice versa?

---

### Post by SlowJet on 2005-11-05
Yes, I have noticed the icon will not stay on the panel after the gui is closed. 
I suspect a Gnome new interaction with the Firestarter old.

Firestarter is the gui config tool for iptables. After configuring and close the gui, Firestarter is not running, only the changed iptables.

in a term do
sudo iptables -L
and you will see a lot of items concerning ports.
Look for the items you setup.
(Btw: I did the List and it slowed to a claw for ouputing so give it few seconds.)

Yes, port 80 is used by chats, but other ports are used for other functions.
Also, a chat can be set to use a other potocols if needed.
So basic chat over port 80 may work.
On my Linux and windows chats (MSN Messager, IRC, AOL - what evr format) do not work anymore because of a new ISP router I was required to install.

I would need a port ot two for each type to fit my gateway/proxy requirement (as it only allows certain protocols) and I would need a set  or range of ports for, say,  MSN Messager, to use file sending and recieving, picture send and reciveing, e-mail, and so forth. The effort to confront the ISP and get into my router is a daughting task vs. the need for chat so I have not done it yet. :) )

Here is my IPTABLES _L
You can see I am using SMB, SSH, And few VNC attemps.

~$ sudo iptables -L
Chain INBOUND (1 references)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     all  --  BINKY-48.WINPROXY    anywhere
ACCEPT     tcp  --  BINKY-48.WINPROXY    anywhere            tcp dpt:ssh
ACCEPT     udp  --  BINKY-48.WINPROXY    anywhere            udp dpt:ssh
ACCEPT     tcp  --  URANUS-37.WINPROXY   anywhere            tcp dpts:netbios-ns:netbios-ssn
ACCEPT     udp  --  URANUS-37.WINPROXY   anywhere            udp dpts:netbios-ns:netbios-ssn
ACCEPT     tcp  --  URANUS-37.WINPROXY   anywhere            tcp dpt:microsoft-ds
ACCEPT     udp  --  URANUS-37.WINPROXY   anywhere            udp dpt:microsoft-ds
ACCEPT     tcp  --  BINKY-48.WINPROXY    anywhere            tcp dpts:netbios-ns:netbios-ssn
ACCEPT     udp  --  BINKY-48.WINPROXY    anywhere            udp dpts:netbios-ns:netbios-ssn
ACCEPT     tcp  --  BINKY-48.WINPROXY    anywhere            tcp dpt:microsoft-ds
ACCEPT     udp  --  BINKY-48.WINPROXY    anywhere            udp dpt:microsoft-ds
ACCEPT     tcp  --  Celcila-24           anywhere            tcp dpt:5500
ACCEPT     udp  --  Celcila-24           anywhere            udp dpt:5500
LSI        all  --  anywhere             anywhere

Chain INPUT (policy DROP)
target     prot opt source               destination
ACCEPT     tcp  --  URANUS-37.WINPROXY   anywhere            tcp flags:!SYN,RST,ACK/SYN
ACCEPT     udp  --  URANUS-37.WINPROXY   anywhere
ACCEPT     all  --  anywhere             anywhere
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5
DROP       all  --  anywhere             255.255.255.255
DROP       all  --  anywhere             90.255.255.255
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8
DROP       all  --  255.255.255.255      anywhere
DROP       all  --  anywhere             0.0.0.0
DROP       all  --  anywhere             anywhere            state INVALID
LSI        all  -f  anywhere             anywhere            limit: avg 10/min burst 5
INBOUND    all  --  anywhere             anywhere
LOG_FILTER  all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Input'

Chain FORWARD (policy DROP)
target     prot opt source               destination
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5
LOG_FILTER  all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Forward'

Chain LOG_FILTER (5 references)
target     prot opt source               destination

Chain LSI (2 references)
target     prot opt source               destination
LOG_FILTER  all  --  anywhere             anywhere
LOG        tcp  --  anywhere             anywhere            tcp flags:SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound '
DROP       tcp  --  anywhere             anywhere            tcp flags:SYN,RST,ACK/SYN
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound '
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound '
DROP       icmp --  anywhere             anywhere            icmp echo-request
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound '
DROP       all  --  anywhere             anywhere

Chain LSO (0 references)
target     prot opt source               destination
LOG_FILTER  all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound '
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable

Chain OUTBOUND (1 references)
target     prot opt source               destination
ACCEPT     icmp --  anywhere             anywhere
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     all  --  anywhere             anywhere

Chain OUTPUT (policy DROP)
target     prot opt source               destination
ACCEPT     tcp  --  Celcila-24           URANUS-37.WINPROXY  tcp dpt:domain
ACCEPT     udp  --  Celcila-24           URANUS-37.WINPROXY  udp dpt:domain
ACCEPT     all  --  anywhere             anywhere
DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere
DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8
DROP       all  --  255.255.255.255      anywhere
DROP       all  --  anywhere             0.0.0.0
DROP       all  --  anywhere             anywhere            state INVALID
OUTBOUND   all  --  anywhere             anywhere
LOG_FILTER  all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Output'
darwinhwebb@Celcila-24:~$

---

### Post by SlowJet on 2005-11-05
This link may help some people setup Firestarter to fit their needs.
 [http://www.emsisoft.com/en/kb/portlist/Default.aspx](http://www.emsisoft.com/en/kb/portlist/Default.aspx) 

Notice the radio buttons at the top of the list.

Notice port 1863 is one for MSN Messager
And the ports
6891-6900 are used

6667 - mIRC chat, MSN Gamezone

5500 -5503 VNC
5800-5899 JAva VNC
5900-5999 regular VNC server 

20000 - ICQ

chat - 531 ??
private chat - 1735
Yawhoo messenger chat - 5001

---

### Post by kroiz on 2005-11-06
[QUOTE=SlowJet]
in a term do
sudo iptables -L
and you will see a lot of items concerning ports.
[/QUOTE]
here is my sudo iptables -L:
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

some how it is empty although I have the rules in firestarter (which is closed).

also I noticed that when I get to work. Yahoo DOES connect.:confused:
Maybe it is because at work, I connect to the LAN/internet, using eth0 while at home I use eth1.
does this help?
Because in firestarter preferences-> network settings, the device that is defined for internet connection, is eth1 (used at home).

---

### Post by SlowJet on 2005-11-06
[QUOTE=kroiz]here is my sudo iptables -L:
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

some how it is empty although I have the rules in firestarter (which is closed).

also I noticed that when I get to work. Yahoo DOES connect.:confused:
Maybe it is because at work, I connect to the LAN/internet, using eth0 while at home I use eth1.
does this help?
Because in firestarter preferences-> network settings, the device that is defined for internet connection, is eth1 (used at home).[/QUOTE]


The only thing I can imagine is that you did not clcik on the APPLY button to tell Firestarter to use the new changes.

Try that with the gui and don't touch anything else
then do
sudo iptables -L

g/l

SJ

---

### Post by kroiz on 2005-11-06
[QUOTE=SlowJet]The only thing I can imagine is that you did not clcik on the APPLY button to tell Firestarter to use the new changes.

Try that with the gui and don't touch anything else
then do
sudo iptables -L

g/l

SJ[/QUOTE]

No the changes were applied alright.
but anyway I completly uninstalled FireStarter and still no connection to yahoo.

---

### Post by SlowJet on 2005-11-06
[QUOTE=kroiz]No the changes were applied alright.
but anyway I completly uninstalled FireStarter and still no connection to yahoo.[/QUOTE]


OK, but for others that venture by,

Any program that requires ports open for inbound listening can only get those open via the iptables.

Firestarter is the easiest gui tool around.
Although, it only handles one interface (multiple promised in the next version).
So it could be the default eth0 is needed. 

If Firestarter rules were applied and the firewall restarted then the iptables -L would show the change or there would be some error in the /var/log/firestarter.


The next best fw (iptables) is a scritp someone wrote in the how-to tips and tricks big long thread.

Lastly, if you are connected to a router, the ports need to be open there too.

If you want yawhoo badly enough, try again after configuring the eth0.
Make sure you install Firestarter as sudo apt-get firestarter.
When you first open it from the menu it should ask for you password or something is wrong with the sudo process.

SJ

---

