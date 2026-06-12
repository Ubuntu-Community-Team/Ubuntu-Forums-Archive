---
title: "HOW-TO: Fujitsu-Siemens ESPRIMO Mobile Wifi+Ethenet setup with ndiswrapper in Feisty"
date: 2007-10-16
forum: Hardware &amp; Laptops
---

### Post by enrico.sanguin on 2007-10-16
SiS191 Gigabit Ethernet (PCI ID: 1039:0191) and Atheros wireless (PCI ID: 168c:001c) hardware are not supported by Ubuntu Feisty Desktop after installation because it try to use Atheros Madwifi drivers ([http://madwifi.org/](http://madwifi.org/)) and Sis190/191 linux drivers ([www.sis.com](www.sis.com)). After an update of these drivers the cards still not work.

I WORKAROUND the problem with ndiswrapper 1.48 built from source (it is designed for wirless NICs but it's so good that it can drive that wired NICs too!!).

Steps:
- blacklist "ath_pci" and "sis190" modules in /etc/modprobe.d/blacklist
- Unload those modules with "modprobe -r"
- Download the windows XP drivers of the cards from fujitsu-siemens ("WN2302A-F4 13ch. mPCI WLAN IEEE802.11 b/g" and "SiS 196"), extract the directories with the .inf file and copy them to your laptop home (maybe using an USB stick).
- Download and copy to your laptop home the ndiswrapper 1.48 tarball (from [http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/))
- Unpack it with "tar -xzf" and remember to "make unistall" (to delete the ndiswrapper module shpped with Feisty) before "make" and "make install".
- Refresh module dependecy file with depmod -a
- Install both drivers using "ndiswrapper -i <path to windows driver .inf file>" (net5211.inf and sisgbe.inf).
- verify that "ndiswrapper -l" return:

net5211 : driver installed
        device (168C:001C) present (alternate driver: ath_pci)
sisgbe : driver installed
        device (1039:0191) present (alternate driver: sis190)

- Load ndiswrapper module with "modprobe ndiswrapper" and see with "dmesg" if drivers load successfully.
- Now "ifconfig" must show two new devices: wlan0 and wlan1. Configure them with Gnome network manager or with the tools you prefer and test your connection.
- Once you are satisfied, write ndiswrapper module configuration with "ndiswrapper -m" and add "ndiswrapper" to the list of modules to load at startup (/etc/modules).
- Reboot
- EOF

Hope this helps.
Bye!

---

### Post by Espinha on 2007-11-01
Fantastic guide! I have an ESPRIMO Mobile V5515 and it worked like a charm! Thank you so much :)

---

### Post by aspro648 on 2007-12-03
> 
- Once you are satisfied, write ndiswrapper module configuration with "ndiswrapper -m" and add "ndiswrapper" to the list of modules to load at startup (/etc/modules).


Can you give a little more detail on how to do this step for a noobie?
Thanks!

---

### Post by enrico.sanguin on 2007-12-09
Simply append the word "ndiswrapper" to the /etc/modules file.
This file contains the list of modules to be loaded on boot.
Hope this helps.
Bye!

---

### Post by santoxyz on 2007-12-31
the wired network problem can be solved also patching and recompiling the kernel:

the problem is that the driver uses the wrong address for the ISA bridge and the solution is something like:

edit ($KERNEL_SOURCES)/drivers/net/sis190.c
(usually, after you installed linux-source, KERNEL_SOURCES=/usr/src/linux)

and, near line 1593 , in function 
            static int __devinit sis190_get_mac_addr_from_apc

in line
            isa_bridge = pci_get_device(PCI_VENDOR_ID_SI, 0x0965, NULL);

substitute the address 0x0965 with yours.

but which is yours ???
you can discover it doing something like
            lspci -nn | grep -i isa 


after saving recompile the kernel (make && make modules) and copy the newly compiled module (sis190.ko) into /lib/modules/<kernel_version>...
now 
   rmmod sis190 && modprobe sis190 (or reboot to be much secure...)

and the eth0 should be fully functional!!!!
   

sorry for the ugly post (i have not a v5515 under my eyes and i'm searching into my mind.... and my memory isn't much good! ) and the ugly english.

---

### Post by santoxyz on 2007-12-31
a question: is there good support for the esprimo video card?
which is the best driver? it supports 3D indirect rendering?

---

### Post by memala on 2008-01-08
Hi,

enrico.sanguin fantastic tutorial. I still good following problem:
Ping works but ssh and http connection don't work, does any knows a reason for this? Can this some how be related to the ndiswrapper module?
From where does ubuntu knows which interface (lan or wlan) it should use for the ssh connection?

(Sorry for the long posting.)


=====MY SETTINGS
- I got a Fujitsu-Siemens Esprimo Mobile V5535 laptop

- I use 7.10 Gutsy Gibbon (original cd, no modifications)

- I used the standard ndiswrapper which is on the Ubuntu Gutsy cd.

- The ubuntu laptop is called "ubuntu" (on a second partition it has additional winXp installed ) => IP: 192.168.1.100
  A other computer (with debian etch) is called "debian". => IP: 192.168.1.10

- A ping from "debian" to "ubuntu" (and vice verse) works => network connections seems to be ok.

- A ssh connection from "debian" to "ubuntu" (and vice verse) does not work.
  The ssh logins are non-root (normal users).
  
- With firefox on "ubuntu" I tried to open the apache start page from "debian" => this did not work
  From the winXp on the "ubuntu" laptop the apache start page on "debian" is reachable => webserver setup on "debian" is correct.


  
=====NETWORK SETTINGS
After using your guide, two new interfaces appeared (lan network=wlan0, wlan=wlan1).

$ sudo ifconfig wlan0 192.168.1.100 netmask 255.255.255.0 up

root@ubuntu:~$ ifconfig 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:541 errors:0 dropped:0 overruns:0 frame:0
          TX packets:541 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:52947 (51.7 KB)  TX bytes:52947 (51.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:A0:D1:C9:33:D3  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2a0:d1ff:fec9:33d3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:330 errors:0 dropped:0 overruns:0 frame:0
          TX packets:424 errors:0 dropped:3 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:30653 (29.9 KB)  TX bytes:86267 (84.2 KB)
          Interrupt:22 Memory:d4407000-d4407080 

wlan1     Link encap:Ethernet  HWaddr 00:16:44:10:EB:C2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Memory:d4100000-d4110000 




=====PING WORKS
Ping on "ubuntu" to "debian" works => network connection seem to work.

user@ubuntu:~$ ping 192.168.1.10
PING 192.168.1.10 (192.168.1.10) 56(84) bytes of data.
64 bytes from 192.168.1.10: icmp_seq=1 ttl=64 time=0.256 ms
64 bytes from 192.168.1.10: icmp_seq=2 ttl=64 time=0.243 ms
64 bytes from 192.168.1.10: icmp_seq=3 ttl=64 time=0.236 ms
64 bytes from 192.168.1.10: icmp_seq=4 ttl=64 time=0.276 ms
64 bytes from 192.168.1.10: icmp_seq=5 ttl=64 time=0.252 ms
64 bytes from 192.168.1.10: icmp_seq=6 ttl=64 time=0.248 ms
^X
--- 192.168.1.10 ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 4999ms
rtt min/avg/max/mdev = 0.236/0.251/0.276/0.024 ms




====SSH CONNECTION TO "debian" =>DOESN'T WORK
The ssh connection from "ubuntu" to "debian" does not work. After starting the ssh connection nothing happens no output, no error message and no login!

user@ubuntu:~$ ssh -vvv user@192.168.1.10
OpenSSH_4.6p1 Debian-5build1, OpenSSL 0.9.8e 23 Feb 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.1.10 [192.168.1.10] port 22.
debug1: Connection established.
debug1: identity file /home/user/.ssh/identity type -1
debug1: identity file /home/user/.ssh/id_rsa type -1
debug1: identity file /home/user/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.3p2 Debian-9
debug1: match: OpenSSH_4.3p2 Debian-9 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.6p1 Debian-5build1
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent





=====FIREWALL
To be sure that the firewall does not cause any trouble I deactivated it. => ssh still don't work

root@ubuntu:/home/user# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         


root@ubuntu:/home/user# iptables -F





=====SSH SERVER CORRECT INSTALLED ON "ubuntu"? =>YES
To test this I made a ssh to localhost on "ubuntu". This worked. => ssh server is installed correct on "ubuntu".

[email]user@ubuntu:/media/disk/.tmp[/email]/ubuntuConfig$ ssh -vvv user@localhost
OpenSSH_4.6p1 Debian-5build1, OpenSSL 0.9.8e 23 Feb 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to localhost [127.0.0.1] port 22.
debug1: Connection established.
debug1: identity file /home/user/.ssh/identity type -1
debug1: identity file /home/user/.ssh/id_rsa type -1
debug1: identity file /home/user/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.6p1 Debian-5build1
debug1: match: OpenSSH_4.6p1 Debian-5build1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.6p1 Debian-5build1
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: mac_init: found hmac-md5
debug1: kex: server->client aes128-cbc hmac-md5 none
debug2: mac_init: found hmac-md5
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug2: dh_gen_key: priv key bits set: 131/256
debug2: bits set: 509/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug3: check_host_in_hostfile: filename /home/user/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 1
debug1: Host 'localhost' is known and matches the RSA host key.
debug1: Found key in /home/user/.ssh/known_hosts:1
debug2: bits set: 509/1024
debug1: ssh_rsa_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /home/user/.ssh/identity ((nil))
debug2: key: /home/user/.ssh/id_rsa ((nil))
debug2: key: /home/user/.ssh/id_dsa ((nil))
debug1: Authentications that can continue: publickey,password
debug3: start over, passed a different list publickey,password
debug3: preferred gssapi-keyex,gssapi-with-mic,gssapi,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /home/user/.ssh/identity
debug3: no such identity: /home/user/.ssh/identity
debug1: Trying private key: /home/user/.ssh/id_rsa
debug3: no such identity: /home/user/.ssh/id_rsa
debug1: Trying private key: /home/user/.ssh/id_dsa
debug3: no such identity: /home/user/.ssh/id_dsa
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password
user@localhost's password: 
debug3: packet_send2: adding 64 (len 59 padlen 5 extra_pad 64)
debug2: we sent a password packet, wait for reply
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug3: ssh_session2_open: channel_new: 0
debug2: channel 0: send open
debug1: Entering interactive session.
debug2: callback start
debug2: client_session2_setup: id 0
debug2: channel 0: request pty-req confirm 0
debug3: tty_make_modes: ospeed 38400
debug3: tty_make_modes: ispeed 38400
debug3: tty_make_modes: 1 3
debug3: tty_make_modes: 2 28
debug3: tty_make_modes: 3 127
debug3: tty_make_modes: 4 21
debug3: tty_make_modes: 5 4
debug3: tty_make_modes: 6 255
debug3: tty_make_modes: 7 255
debug3: tty_make_modes: 8 17
debug3: tty_make_modes: 9 19
debug3: tty_make_modes: 10 26
debug3: tty_make_modes: 12 18
debug3: tty_make_modes: 13 23
debug3: tty_make_modes: 14 22
debug3: tty_make_modes: 18 15
debug3: tty_make_modes: 30 0
debug3: tty_make_modes: 31 0
debug3: tty_make_modes: 32 0
debug3: tty_make_modes: 33 0
debug3: tty_make_modes: 34 0
debug3: tty_make_modes: 35 0
debug3: tty_make_modes: 36 1
debug3: tty_make_modes: 37 0
debug3: tty_make_modes: 38 1
debug3: tty_make_modes: 39 1
debug3: tty_make_modes: 40 0
debug3: tty_make_modes: 41 1
debug3: tty_make_modes: 50 1
debug3: tty_make_modes: 51 1
debug3: tty_make_modes: 52 0
debug3: tty_make_modes: 53 1
debug3: tty_make_modes: 54 1
debug3: tty_make_modes: 55 1
debug3: tty_make_modes: 56 0
debug3: tty_make_modes: 57 0
debug3: tty_make_modes: 58 0
debug3: tty_make_modes: 59 1
debug3: tty_make_modes: 60 1
debug3: tty_make_modes: 61 1
debug3: tty_make_modes: 62 0
debug3: tty_make_modes: 70 1
debug3: tty_make_modes: 71 0
debug3: tty_make_modes: 72 1
debug3: tty_make_modes: 73 0
debug3: tty_make_modes: 74 0
debug3: tty_make_modes: 75 0
debug3: tty_make_modes: 90 1
debug3: tty_make_modes: 91 1
debug3: tty_make_modes: 92 0
debug3: tty_make_modes: 93 0
debug1: Sending environment.
debug3: Ignored env SSH_AGENT_PID
debug3: Ignored env SHELL
debug3: Ignored env DESKTOP_STARTUP_ID
debug3: Ignored env TERM
debug3: Ignored env XDG_SESSION_COOKIE
debug3: Ignored env GTK_RC_FILES
debug3: Ignored env WINDOWID
debug3: Ignored env OLDPWD
debug3: Ignored env USER
debug3: Ignored env LS_COLORS
debug3: Ignored env SSH_AUTH_SOCK
debug3: Ignored env GNOME_KEYRING_SOCKET
debug3: Ignored env SESSION_MANAGER
debug3: Ignored env USERNAME
debug3: Ignored env PATH
debug3: Ignored env DESKTOP_SESSION
debug3: Ignored env GDM_XSERVER_LOCATION
debug3: Ignored env PWD
debug1: Sending env LANG = en_US.UTF-8
debug2: channel 0: request env confirm 0
debug3: Ignored env GNOME_KEYRING_PID
debug3: Ignored env GDM_LANG
debug3: Ignored env GDMSESSION
debug3: Ignored env HISTCONTROL
debug3: Ignored env SHLVL
debug3: Ignored env HOME
debug3: Ignored env GNOME_DESKTOP_SESSION_ID
debug3: Ignored env LOGNAME
debug3: Ignored env XDG_DATA_DIRS
debug3: Ignored env DBUS_SESSION_BUS_ADDRESS
debug3: Ignored env LESSOPEN
debug3: Ignored env WINDOWPATH
debug3: Ignored env DISPLAY
debug3: Ignored env LESSCLOSE
debug3: Ignored env COLORTERM
debug3: Ignored env XAUTHORITY
debug3: Ignored env _
debug2: channel 0: request shell confirm 0
debug2: fd 3 setting TCP_NODELAY
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768
debug2: channel 0: rcvd adjust 131072
Linux ubuntu 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
Last login: Mon Jan  7 21:25:46 2008 from ubuntu.local
user@ubuntu:~$ 



====SSH DAEMON STARTED ON "ubuntu" => YES
The pstree command shows that the "sshd" is running.

root@ubuntu:/home/user# pstree

init-+-NetworkManager---{NetworkManager}
     |-NetworkManagerD
     |-acpid
     |-atd
     |-avahi-daemon---avahi-daemon
     |-bonobo-activati---{bonobo-activati}
     |-console-kit-dae---61*[{console-kit-dae}]
     |-cron
     |-cupsd
     |-2*[dbus-daemon]
     |-dd
     |-deskbar-applet
     |-dhcdbd
     |-firefox---run-mozilla.sh---firefox-bin---6*[{firefox-bin}]
     |-2*[gconfd-2]
     |-gdm---gdm-+-Xorg
     |           `-x-session-manag-+-bluetooth-apple
     |                             |-evolution-alarm---{evolution-alarm}
     |                             |-gnome-panel
     |                             |-metacity
     |                             |-nautilus
     |                             |-nm-applet
     |                             |-python
     |                             |-ssh-agent
     |                             |-trackerd---2*[{trackerd}]
     |                             |-update-notifier
     |                             |-vino-session
     |                             `-{x-session-manag}
     |-6*[getty]
     |-2*[gksu---network-admin]
     |-gnome-help---2*[{gnome-help}]
     |-gnome-keyboard-
     |-gnome-keyring-d
     |-gnome-power-man
     |-gnome-screensav
     |-gnome-settings----{gnome-settings-}
     |-gnome-terminal-+-bash---su---bash-+-pstree
     |                |                  `-xterm---bash---ssh
     |                |-bash---gedit
     |                |-bash
     |                |-gnome-pty-helpe
     |                `-{gnome-terminal}
     |-gnome-vfs-daemo
     |-gnome-volume-ma
     |-hald---hald-runner-+-hald-addon-acpi
     |                    |-hald-addon-cpuf
     |                    |-5*[hald-addon-keyb]
     |                    `-3*[hald-addon-stor]
     |-hcid---2*[bluetoothd-serv]
     |-klogd
     |-mapping-daemon
     |-mixer_applet2---{mixer_applet2}
     |-multiload-apple
     |-notification-da
     |-sshd
     |-syslogd
     |-system-tools-ba---dbus-daemon
     |-trashapplet
     `-udevd

---

### Post by memala on 2008-01-18
The problem with the nic "sis191" is solved [1].
1: [https://lists.ubuntu.com/archives/ubuntu-users/2008-January/134789.html](https://lists.ubuntu.com/archives/ubuntu-users/2008-January/134789.html)

Emal

---

### Post by afrie on 2008-02-06
The hardy patch instructions posted here <https://lists.ubuntu.com/archives/ubuntu-users/2008-January/134789.html> does not work for me.

I found a solution to activate the ethernet controller SIS 191 [1039:0191] on a FSC notebook V5515 with Ubuntu 7.10 (Gutsy) by running a customized 2.6.24 kernel from kernel.org. If someone is interrested please read 'wget home.teleos-web.de/afriedrich0/afrie_fsc_v5515_sis191_instructions.txt'.

---

