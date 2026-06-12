---
title: "internet suddenly stopped working after setting up a dual boot"
date: 2008-10-15
forum: General Help
---

### Post by gsrcrxsi on 2008-10-15
so ever since i installed server 2008 (on a separate drive mind you) my internet has not worked in linux. my distro is Xubuntu for all intensive purposes (technically mythbuntu). the internet works fine in windows, but when in linux, it tried to load the page but times out. "ifconfig" shows my IP address from my router, so it has a connection, but for whatever reason its not giving me access to the internet, i cant even log into the router. its not a browser setting because pidgin wont connect either. i really dont know where to begin on this one. any ideas?

---

### Post by jerome1232 on 2008-10-15
Well can you ping the router/internet, that last ip is one of google's ip's. Also what happens when you request an address

```
ping -c 1 [router ip here]
ping -c 1 google.com
ping -c 1 72.14.207.99
sudo dhclient eth0
```

---

### Post by gsrcrxsi on 2008-10-15
the computer is setup as static IP and i want to keep it that way. its a server and it has to communicate with other computers, static IP is much easier that way. ill try that ping command.

---

### Post by gsrcrxsi on 2008-10-15
ping was unsuccessful. 

i tried unplugging the ethernet and plugging it into the other lan port on my MB and it worked fine, (but not static) i dont know whats going on.

---

### Post by jerome1232 on 2008-10-15
Ok lets take a look at a few things, it's probably something about the static address is wrong. Some of the output from these commands should give us a hint as to what's going on.

```
ifconfig  # while connected via dhcp I think it'll show your static info as well
route  # while connected staticly and while connected via dhcp
cat /etc/network/interfaces
cat /etc/resolv.conf
```

edit: I thought you were using dhcp at first because you said '"ifconfig" shows my IP address from my router', that and it's what most people use.

---

### Post by gsrcrxsi on 2008-10-17
static info is not wrong. its what i want it to be 192.168.1.100

i may have just "fixed" it. although i had to change the settings from what they were to something else. before i had it setup as a static IP, both in my router and in linux.

my "fix" was to put the computer on roaming mode (dhcp) and tell the dhcp server in the router to always give its mac address the same IP. this is not the solution id hoped for, as i would rather have figured out what went wrong and why its not working but this will do i suppose.

however, now the internet doesnt work when i boot into windows. wtf is going on?

---

### Post by dave.com on 2008-10-17
Weelp, did you install winbindd(?) and if not has it installed itself as a sneaking, shady package dependency you mighta not noticed, and do you have samba shares or something, or a rogue firewall app, or did you perchance install auto ppp or something, and did you order pizza over the net recently (hey, you never know)?

This is so complicated...

---

### Post by gsrcrxsi on 2008-10-17
i have no idea what you are talking about... 

winbind is installed. should i uninstall it? what is it?
no i dont have samba shares.
no firewall app in linux.in windows there is, but thats not the issue since it worked before
no i didnt order pizza.

---

### Post by dave.com on 2008-10-17
winbindd has to do with windows service sharing across OS filesystems which you don't need unless your dualboot is a network to itself for itself by itself 
ugetme? => It may be a kinda race between windows and ubuntu which one is the boss (client/host) next time you launch another OS platform.

---

### Post by jerome1232 on 2008-10-17
I say it's something about the static address because if dhcp works, then the static address has something wrong with it. ie it's not on the right subnet, the route/default gateway is wrong, another machine on the network has the address (so the router is sending the other computer the responses to your ping requests, and all other traffic for that matter).

Something is wrong with the static assignment.

I actually use to use dhcp to reserve ip's by mac address and I liked having a central place to manage ip's. Now I use a box as a dhcp server that dynamically updates a dns server, so I don't refer to machines by ip, but by name and it's always correct regardless of their current ip.

---

### Post by gsrcrxsi on 2008-10-17
well like i said im not using the static assignment anymore, im using DHCP and the dhcp server is assigning a "static" ip based on the mac address. everything is fine and dandy now in linux, however now when i boot the same machine into windows it will not connect. thats what im trying to solve now. and im sure if i do a fix in windows it will break linux. i just want them both to work without me having to fix it every time.

---

### Post by jerome1232 on 2008-10-17
Is Windows also using a static assignment or is it using dhcp? Since they are the same machine it should be grabing the same ip Linux was. Try simple ipconfigs to see if it's getting a response from the router.

```
ipconfig/release
ipconfig/renew
```

---

### Post by gsrcrxsi on 2008-10-18
hmm i think it was using dhcp. i never messed with it, im pretty sure it uses dhcp by default. ill have to try it when i get it booted back into windows, im currently doing a drive migration of my linux partition to a new drive lol.

---

### Post by TeXtonyx on 2008-10-18
Just an idea from reading other internet access problems with Linux
and Windows. Try sudo dhclient -r eth0 , the Linux equivalent of
ipconfig/release, when you log off Linux. Some of the situations
resolved themselves if people waited 15-30 minutes also, so the
lease may not be expiring in a timely fashion. Easy enough to try.

---

### Post by dave.com on 2008-10-18
My modem has a built-in router, I got a very similar problem on my dualbooter and I got rid of winbind (not suggesting that is the answer, mind). After setting up wired network configuration I moved my browser home address too. But that's by the by, my connection wizard setup (modem's software) now opened on the Browser home page ya see (after I got net back up). 

Assuming your network is active, but not going anywhere (and you have Gnome) go to Admin/System - Network tools, set eth0 on 1st tab, next tab ping your gateway address and local host and finally the ip address. In Desktop go to the little net icon and select manual network, open your saved network (you have one, yeh?), see Wired connection icon (highlight it) Properties looks okay and go see Properties on the modem icon underneath that (just highlight it and click Properties). On the last tab make sure the modem checkbox is unset ie. is not handling the dns biz, and the button underneath it is set. 
Set local host with the user alias for your isp account user name (eg. "local host joe" not the whole dang thing just the bit in front of @) rather than the ubuntu box hostname (last tab in that buncha tabs above the Wired/modem icons), add the isp address minus www ("isp-address.com")below it and once again for ip with username leading (joe.isp-adress.com) below that. NB: Wired config Properties should have a) ip address b)broadcast mask c) gateway address and the full isp [email]user@xx.isp-address.com[/email] account name. The route addressing requested by Windows is different: a)gateway b)subnet Mask c) ip address. 
ie. Ubuntu asks the info from the other end up. 

You will need primary and secondary dns addresses as well. List your Search Domains under these with your gateway and ip addresses (throw in your local host and loopback as well if you want).

I'm trying to give ya the scope from memory because <cough> atm my /home/root is not owned by root and instead of X-gdm I get a tty login that's emailing everything back (my comp and I are not 'talking' to each other /blush).

---

