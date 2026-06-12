---
title: "Two maching to much security, I think?"
date: 2005-11-05
forum: General Help
---

### Post by irv on 2005-11-05
I have spent much time trying to figure this problem out, and it's got to be something I am missing.
I am trying to Network two computer, but can't FTP or use Samba or NTS.( it could be a rights issue.)
I have Ubuntu running on both machines: one is a desktop the other a server. Both have Breezy 5.10.
My connection is is done via NIC cards going through a D-link Router. My router is setup with ports 21-FTP, 443-HTTPS, 53-DNS, 25-SMTP, 110-POP3, 23-Telnet, 80-HTTP and are all open to ip 192.168.0.100 which is the static address of my server. I can ping and use VNCViewer with no problem.
I have a Samba server, FTP server, HTTP server, Mail server, NTS, etc running on the server and  I can't get from my desktop to my server with Samba, NTS, Telnet, or FTP. I can see web pages via HTTP, so port 80 is open. I have tried open ports with iptables, and even installed Firestarter but can't figure out how to open ports. 
I read a thread about doing a iptables -F to clean and start over, but then it said to &#8220;system-config-securitylevel and just enable firewall nothing else.&#8221; but for the life of me I can't find anything like that on either my server or desktop. Am I missing a install or something?
I have tried every step-by-step I can find and I am not getting no where. Can somebody give me a push in the right direction? 
I love both my setups and I don't want to go back to "suse" I want to stay with Ubuntu. Hope someone can help:???:

---

### Post by irv on 2005-11-07
I have had this thread on the forum for two days now and it seem no one has an answer for me on my server/desktop issue. (see above).
Can anyone help.
Thanks

---

### Post by simms on 2005-11-07
[QUOTE=irv]I have had this thread on the forum for two days now and it seem no one has an answer for me on my server/desktop issue. (see above).
Can anyone help.
Thanks[/QUOTE]

no offense, but you're not going to get much help if you can't describe the nature of your problem properly.  i've read your post three times and i still can't understand what you're trying to accomplish, exactly.  i doubt that changing linux distros will help you at all.

---

### Post by irv on 2005-11-07
I am sorry it wasn't clear, so I edited the original message. Hope this helps. It is a networking problem I am having. Can use VNCViewer and can use "putty" from the server to the desktop, but can't use "putty" from the desktop to the server. It must be something is not set right on the server.

---

### Post by poptones on 2005-11-07
I think the problem here is the /etc/default/portmap gotcha...

Open /etc/default/portmap and remove the line "-i 127.0.0.1"

---

### Post by steve.horsley on 2005-11-07
[QUOTE=irv]I am sorry it wasn't clear, so I edited the original message. Hope this helps. It is a networking problem I am having. Can use VNCViewer and can use "putty" from the server to the desktop, but can't use "putty" from the desktop to the server. It must be something is not set right on the server.[/QUOTE]

Is the server running servers for SSH (and VNC)? Perhaps the easiest way to find out is to use the command
   **sudo netstat -pant**
Post the resulting output here.

---

### Post by irv on 2005-11-07
root@wabasha-server:/etc/default# netstat -pant
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State PID/Program name
tcp        0      0 0.0.0.0:2049            0.0.0.0:*               LISTEN     - 
tcp        0      0 127.0.0.1:32769         0.0.0.0:*               LISTEN     6 860/hpiod
tcp        0      0 127.0.0.1:32770         0.0.0.0:*               LISTEN     6 882/python
tcp        0      0 0.0.0.0:32771           0.0.0.0:*               LISTEN     - 
tcp        0      0 0.0.0.0:742             0.0.0.0:*               LISTEN     6 921/ypbind
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN     7 453/mysqld
tcp        0      0 127.0.0.1:587           0.0.0.0:*               LISTEN     7 828/sendmail: MTA:
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN     7 725/smbd
tcp        0      0 0.0.0.0:5900            0.0.0.0:*               LISTEN     2 8786/vino-server
tcp        0      0 0.0.0.0:718             0.0.0.0:*               LISTEN     7 744/rpc.statd
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN     5 965/portmap
tcp        0      0 0.0.0.0:10000           0.0.0.0:*               LISTEN     7 833/perl
tcp        0      0 0.0.0.0:950             0.0.0.0:*               LISTEN     7 555/rpc.mountd
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     3 193/cupsd
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN     7 828/sendmail: MTA:
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN     7 725/smbd
tcp        0      0 127.0.0.1:49992         127.0.0.1:32769         ESTABLISHED6 882/python
tcp        0      0 127.0.0.1:32769         127.0.0.1:49992         ESTABLISHED6 860/hpiod
tcp        0      0 127.0.0.1:631           127.0.0.1:33171         ESTABLISHED3 193/cupsd
tcp       10      0 192.168.0.100:5900      192.168.0.102:39681     ESTABLISHED2 8786/vino-server
tcp        0      0 127.0.0.1:33171         127.0.0.1:631           ESTABLISHED7 294/gnome-cups-ico
tcp6       0      0 :::80                   :::*                    LISTEN     1 6510/apache2

---

### Post by Zwack on 2005-11-07
[QUOTE=irv]root@wabasha-server:/etc/default# netstat -pant
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State PID/Program name
[/QUOTE]

Given that ssh runs on port 22 and isn't running, and that VNC (by default) uses port 5900 and it's not running, I'm not surprised you can't connect to them...

Make sure that the servers are installed, configured and running... then try.

If you think that they are then try running ssh localhost and vncviewer localhost and seeing if the server can connect to itself.  Once it can then try from the client PC...  If that is not working then start looking at the firewall.

Z.

---

### Post by irv on 2005-11-08
I can connect via vncviewer from the client and the server, but I can't make a connection from the client or the server using ssh.
From the client I just type vncviewer ipaddress and it connects.
If I type ssh localhost or ipaddress I get "ssh: connect to host 192.168.0.100 port 22: Connection refused." If it is the firewall and a port could you give me some direction? Should I write a scrip to run at boot time to open ports or just edit hosts.allow to open to my client PC? I have been trying different things but nothing seems to work.
Thanks

---

### Post by _MiniMe_ on 2005-11-08
I think what Zwack was trying to say, is that the ssh-server seems not to be running on your sever-machine (because it's not in the list you posted). Are you sure that you've installed the "openssh-server" package? You can use 

```
dpkg --status openssh-server
```
to see if the package is installed. Or try

```
ps -A | grep sshd
```
to see if the ssh-server is running.

If you want to open all Ports on your Server, the easiest way to do this is to change the policy of the INPUT chain.

```
iptables --policy INPUT ACCEPT 
```
(not sure if its "ACCEPT" or "accept")

BTW: An easy way to administrate a server is the use of webmin. You can get it via Synaptic or at [http://www.webmin.com/](http://www.webmin.com/)

good luck

---

### Post by irv on 2005-11-08
OK, now! I have ssh running on the server and can connect to itself, and I can connect to the ssh from client PC, and can connect via vncviewer from the client to server and vis-vesa, but I still have a problem when I run sshfs from the client to the server. I get the following message:
irv@ubuntu:~$ sudo sshfs irv@wabasha-server: / mountpoint
The authenticity of host 'wabasha-server (192.168.0.100)' can't be established.
RSA key fingerprint is 92:d8:a2:84:b4:8b:be:eb:38:30:8f:44:5d:90:7b:47.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'wabasha-server' (RSA) to the list of known hosts.
irv@wabasha-server's password:
Request for subsystem 'sftp' failed on channel 0
end of file read

---

### Post by irv on 2005-11-08
[QUOTE=irv]OK, now! I have ssh running on the server and can connect to itself, and I can connect to the ssh from client PC, and can connect via vncviewer from the client to server and vis-vesa, but I still have a problem when I run sshfs from the client to the server. I get the following message:
irv@ubuntu:~$ sudo sshfs irv@wabasha-server: / mountpoint
The authenticity of host 'wabasha-server (192.168.0.100)' can't be established.
RSA key fingerprint is 92:d8:a2:84:b4:8b:be:eb:38:30:8f:44:5d:90:7b:47.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'wabasha-server' (RSA) to the list of known hosts.
irv@wabasha-server's password:
Request for subsystem 'sftp' failed on channel 0
end of file read[/QUOTE]
There is a wife like computer on the market.
You don't ask it anything, but it tells you anyway.

---

### Post by irv on 2005-11-09
I just wanted to add what my iptables look like:

irv@wabasha-server:~$ sudo iptables -L
Password:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

---

### Post by irv on 2005-11-09
[QUOTE=irv]I just wanted to add what my iptables look like:

irv@wabasha-server:~$ sudo iptables -L
Password:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination[/QUOTE]
Children are natural mimics; they act like their parents in spite of every effort to teach them good manners.

---

### Post by darkmatter on 2005-11-09
Ok...this has gone far enough...if we cant act like adults and show some courtesy/respect...and general politeness...then this thread is closed...

---

