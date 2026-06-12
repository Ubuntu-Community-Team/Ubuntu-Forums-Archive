---
title: "What the crud..!  My ports are open , why...?"
date: 2008-10-26
forum: General Help
---

### Post by jason.b.c on 2008-10-26
i failed the Shields up test ( [www.grc.com](www.grc.com) )  all of my ports are open except a few , i fail the ICMP test but can pass the others... why...?


i am using the Firestarter package as my iptables front end , how do i configure the firewall for stealth mode...?

---

### Post by jason.b.c on 2008-10-26
> ----------------------------------------------------------------------

GRC Port Authority Report created on UTC: 2008-10-26 at 20:56:08

Results from scan of ports: 0, 21-23, 25, 79, 80, 110, 113, 
                            119, 135, 139, 143, 389, 443, 445, 
                            1002, 1024-1030, 1720, 5000

   23 Ports Open
    0 Ports Closed
    3 Ports Stealth
---------------------
   26 Ports Tested

NO PORTS were found to be CLOSED.

Ports found to be STEALTH were: 135, 139, 445

Other than what is listed above, all ports are OPEN.

TruStealth: FAILED - NOT all tested ports were STEALTH,
                   - NO unsolicited packets were received,
                   - NO Ping reply (ICMP Echo) was received.

----------------------------------------------------------------------



> ----------------------------------------------------------------------

GRC Port Authority Report created on UTC: 2008-10-26 at 20:58:47

Results from scan of ports: 0-1055

 1050 Ports Open
    0 Ports Closed
    6 Ports Stealth
---------------------
 1056 Ports Tested

NO PORTS were found to be CLOSED.

Ports found to be STEALTH were: 135, 136, 137, 138, 139, 445

Other than what is listed above, all ports are OPEN.

TruStealth: FAILED - NOT all tested ports were STEALTH,
                   - NO unsolicited packets were received,
                   - NO Ping reply (ICMP Echo) was received.

----------------------------------------------------------------------


Those are my results...

---

### Post by Nepherte on 2008-10-26
Are you behind a router?

---

### Post by lukjad on 2008-10-26
Well, they *are* selling something. It's in their best interests to scare you. I'm not sure what this means but take it with a grain of salt. If you really want to be secure, there is a version of Ubuntu called nbunto that focuses on security. You may want to check it out.

The main thing you should wonder about is what danger is there if the ports are open.

---

### Post by jason.b.c on 2008-10-26
No , what differance would that make ...?

the firewall is still open...

---

### Post by jason.b.c on 2008-10-26
> **lukjad007 said:**
> Well, they *are* selling something. It's in their best interests to scare you. I'm not sure what this means but take it with a grain of salt. If you really want to be secure, there is a version of Ubuntu called nbunto that focuses on security. You may want to check it out.

The main thing you should wonder about is what danger is there if the ports are open.

this dosen't help me....

---

### Post by jerome1232 on 2008-10-26
That site is probably THE most inaccurate I have ever seen. Use nmap, or just use netstat.

That should tell you what's listening on what port and what interface. This doesn't take your firewall into account.
```
sudo nestat -lpt
```


If you want to see what is open to the internet, go run nmap from a computer connected to the internet elsewhere. Even one on you own lan will work.

```
nmap -A hostsipaddresshere
```

Just to give you an idea though, the internet talks to your router, your router drops all incoming traffic unless you have rules setup in it that say if traffic comes in on port 22, forward it to joe's computer. Then joe's firewall would have to be set to allow connections on port 22, He would also have to have some program listening on port 22. If any one of those things aren't setup the packet gets dropped, aka ignored.

An example netstat output, this shows cups (printer services) listening to localhost (aka won't respond to requests from other computers)

I also have two instances of dvd::rip open, it has a cluster service so that I can have multiple computers work on transcoding dvd's that's the other two ports that are open, they will interact with other computers. As soon as I close dvd::rip those ports will close.

I also have a program that reports on my hddtemps also listening on localhost (not open to the internet)
```
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 *:28646                 *:*                     LISTEN      10769/perl      
tcp        0      0 *:28647                 *:*                     LISTEN      10769/perl      
tcp        0      0 localhost:7634          *:*                     LISTEN      4948/hddtemp    
tcp        0      0 localhost:ipp           *:*                     LISTEN      4784/cupsd  
```

---

### Post by lukjad on 2008-10-26
I was just trying to put it in perspective. Anyway [this thread]("http://ubuntuforums.org/showthread.php?t=396093") looks like it answers a lot of your questions.

---

### Post by p_quarles on 2008-10-26
> **jason.b.c said:**
> No , what differance would that make ...?

the firewall is still open...
It makes a huge difference, as a NAT router is a far better way of securing your home network than a software firewall. 

As explained on the ShieldsUp site, "stealth" essentially means that the port does not send a reply ping to scanning system. This makes it more difficult to determine if a machine is online at the IP address being scanned, so is often a more secure setup for home users. I'm not terribly familiar with Firestarter, but you should be able to find an option that stops reply pings from being sent.

---

### Post by jerome1232 on 2008-10-26
Just as more proof that site is horrible, I actually have ports open, and it's not picking that up....

(I have a router, a server in dmz plus mode, and 3 other computers)

If you ran nmap on tss2.mine.nu I'll bet it comes back with quite a few ports open (that's my host name). When I scan common ports and/or all service ports it comes back as all closed, if I tell it just to scan port 22 it comes back as open (which is correct)

---

### Post by lukjad on 2008-10-26
This site reminds me of a site that "scanned" my Linux box for viruses and found a TON of corrupted dll files that needed fixing for only $29.95! :p

---

### Post by p_quarles on 2008-10-26
> **lukjad007 said:**
> This site reminds me of a site that "scanned" my Linux box for viruses and found a TON of corrupted dll files that needed fixing for only $29.95! :p
I understand the impulse, but Steve Gibson has a good reputation and many people use that site. As pointed out, it may not be 100% accurate, but it's not scamming anyone.

---

### Post by jason.b.c on 2008-10-26
> **jerome1232 said:**
> 

If you want to see what is open to the internet, go run nmap from a computer connected to the internet elsewhere. Even one on you own lan will work.

```
nmap -A hostsipaddresshere
```



even from a windows computer...? , i didn't know that was a windows command...

because i have a 'doze machine at the office...

---

### Post by jason.b.c on 2008-10-26
> **p_quarles said:**
> I understand the impulse, but Steve Gibson has a good reputation and many people use that site. As pointed out, it may not be 100% accurate, but it's not scamming anyone.

i didn't think they were scammers either , i've trusted that site for several years now....

---

### Post by p_quarles on 2008-10-26
> **jason.b.c said:**
> even from a windows computer...? , i didn't know that was a windows command...

because i have a 'doze machine at the office...
I recall seeing a Windows port of nmap a while ago. I'm sure it's there a quick Google search.

---

### Post by jason.b.c on 2008-10-26
> **p_quarles said:**
> I recall seeing a Windows port of nmap a while ago. I'm sure it's there a quick Google search.

[http://nmap.org/download.html](http://nmap.org/download.html)

i found it... :guitar:

---

### Post by lukjad on 2008-10-26
Ah, well, I am in error. I just tend to be skeptical of all internet scans. I have been tricked too many times to be trusting.

---

### Post by jerome1232 on 2008-10-26
> **jason.b.c said:**
> [http://nmap.org/download.html](http://nmap.org/download.html)

i found it... :guitar:

I would also run it on localhost on the machine as well.

If anything shows up on a nmap of localhost and it shows up from the other computer we have a service opened to the internet on your computer.

edit: Sorry didn't notice it my bad :) In that case this doesn't apply. Your on a Windows computer? I thought you were on an Ubuntu one.

---

### Post by jason.b.c on 2008-10-26
> **jerome1232 said:**
>  on other computers connected to your router. You never mentioned if you were directly connected to the internet or behind a router.

```
nmap -A localhost
```



Yes i did mention that , in like my second or third post , i Don't have a router...

---

### Post by ukera on 2008-10-26
Port 139 is open.. Or even "filtered".. not good.  Thats your Netbios port.  I suggest you turn off Printer and file sharing.  It's probably a option turned on behind your router.  Go to your web app for your router, look for "printer and file sharing"  turn that off.

---

### Post by jason.b.c on 2008-10-26
[http://ubuntuforums.org/showthread.php?t=396093](http://ubuntuforums.org/showthread.php?t=396093)

well i read through that whole entire thing , but it still dosen't tell me how to stealth my ports....

---

### Post by jason.b.c on 2008-10-26
well i compiled and installed nmap...

```
jason@HP-Vectra-VL:~$ nmap
Nmap 4.76 ( http://nmap.org )
Usage: nmap [Scan Type(s)] [Options] {target specification}
TARGET SPECIFICATION:
  Can pass hostnames, IP addresses, networks, etc.
  Ex: scanme.nmap.org, microsoft.com/24, 192.168.0.1; 10.0.0-255.1-254
  -iL <inputfilename>: Input from list of hosts/networks
  -iR <num hosts>: Choose random targets
  --exclude <host1[,host2][,host3],...>: Exclude hosts/networks
  --excludefile <exclude_file>: Exclude list from file
HOST DISCOVERY:
  -sL: List Scan - simply list targets to scan
  -sP: Ping Scan - go no further than determining if host is online
  -PN: Treat all hosts as online -- skip host discovery
  -PS/PA/PU [portlist]: TCP SYN/ACK or UDP discovery to given ports
  -PE/PP/PM: ICMP echo, timestamp, and netmask request discovery probes
  -PO [protocol list]: IP Protocol Ping
  -n/-R: Never do DNS resolution/Always resolve [default: sometimes]
  --dns-servers <serv1[,serv2],...>: Specify custom DNS servers
  --system-dns: Use OS's DNS resolver
SCAN TECHNIQUES:
  -sS/sT/sA/sW/sM: TCP SYN/Connect()/ACK/Window/Maimon scans
  -sU: UDP Scan
  -sN/sF/sX: TCP Null, FIN, and Xmas scans
  --scanflags <flags>: Customize TCP scan flags
  -sI <zombie host[:probeport]>: Idle scan
  -sO: IP protocol scan
  -b <FTP relay host>: FTP bounce scan
  --traceroute: Trace hop path to each host
  --reason: Display the reason a port is in a particular state
PORT SPECIFICATION AND SCAN ORDER:
  -p <port ranges>: Only scan specified ports
    Ex: -p22; -p1-65535; -p U:53,111,137,T:21-25,80,139,8080
  -F: Fast mode - Scan fewer ports than the default scan
  -r: Scan ports consecutively - don't randomize
  --top-ports <number>: Scan <number> most common ports
  --port-ratio <ratio>: Scan ports more common than <ratio>
SERVICE/VERSION DETECTION:
  -sV: Probe open ports to determine service/version info
  --version-intensity <level>: Set from 0 (light) to 9 (try all probes)
  --version-light: Limit to most likely probes (intensity 2)
  --version-all: Try every single probe (intensity 9)
  --version-trace: Show detailed version scan activity (for debugging)
SCRIPT SCAN:
  -sC: equivalent to --script=default
  --script=<Lua scripts>: <Lua scripts> is a comma separated list of 
           directories, script-files or script-categories
  --script-args=<n1=v1,[n2=v2,...]>: provide arguments to scripts
  --script-trace: Show all data sent and received
  --script-updatedb: Update the script database.
OS DETECTION:
  -O: Enable OS detection
  --osscan-limit: Limit OS detection to promising targets
  --osscan-guess: Guess OS more aggressively
TIMING AND PERFORMANCE:
  Options which take <time> are in milliseconds, unless you append 's'
  (seconds), 'm' (minutes), or 'h' (hours) to the value (e.g. 30m).
  -T[0-5]: Set timing template (higher is faster)
  --min-hostgroup/max-hostgroup <size>: Parallel host scan group sizes
  --min-parallelism/max-parallelism <time>: Probe parallelization
  --min-rtt-timeout/max-rtt-timeout/initial-rtt-timeout <time>: Specifies
      probe round trip time.
  --max-retries <tries>: Caps number of port scan probe retransmissions.
  --host-timeout <time>: Give up on target after this long
  --scan-delay/--max-scan-delay <time>: Adjust delay between probes
  --min-rate <number>: Send packets no slower than <number> per second
  --max-rate <number>: Send packets no faster than <number> per second
FIREWALL/IDS EVASION AND SPOOFING:
  -f; --mtu <val>: fragment packets (optionally w/given MTU)
  -D <decoy1,decoy2[,ME],...>: Cloak a scan with decoys
  -S <IP_Address>: Spoof source address
  -e <iface>: Use specified interface
  -g/--source-port <portnum>: Use given port number
  --data-length <num>: Append random data to sent packets
  --ip-options <options>: Send packets with specified ip options
  --ttl <val>: Set IP time-to-live field
  --spoof-mac <mac address/prefix/vendor name>: Spoof your MAC address
  --badsum: Send packets with a bogus TCP/UDP checksum
OUTPUT:
  -oN/-oX/-oS/-oG <file>: Output scan in normal, XML, s|<rIpt kIddi3,
     and Grepable format, respectively, to the given filename.
  -oA <basename>: Output in the three major formats at once
  -v: Increase verbosity level (use twice or more for greater effect)
  -d[level]: Set or increase debugging level (Up to 9 is meaningful)
  --open: Only show open (or possibly open) ports
  --packet-trace: Show all packets sent and received
  --iflist: Print host interfaces and routes (for debugging)
  --log-errors: Log errors/warnings to the normal-format output file
  --append-output: Append to rather than clobber specified output files
  --resume <filename>: Resume an aborted scan
  --stylesheet <path/URL>: XSL stylesheet to transform XML output to HTML
  --webxml: Reference stylesheet from Nmap.Org for more portable XML
  --no-stylesheet: Prevent associating of XSL stylesheet w/XML output
MISC:
  -6: Enable IPv6 scanning
  -A: Enables OS detection and Version detection, Script scanning and Traceroute
  --datadir <dirname>: Specify custom Nmap data file location
  --send-eth/--send-ip: Send using raw ethernet frames or IP packets
  --privileged: Assume that the user is fully privileged
  --unprivileged: Assume the user lacks raw socket privileges
  -V: Print version number
  -h: Print this help summary page.
EXAMPLES:
  nmap -v -A scanme.nmap.org
  nmap -v -sP 192.168.0.0/16 10.0.0.0/8
  nmap -v -iR 10000 -PN -p 80
SEE THE MAN PAGE FOR MANY MORE OPTIONS, DESCRIPTIONS, AND EXAMPLES

``` 

so how do i get that fancy GUI like this one...? 

[IMG]http://images.insecure.org/nmap/zenmap/images/zenmap-no-648x700.png[/IMG]

---

### Post by p_quarles on 2008-10-26
That's a front end called Zenmap, which should be in the Ubuntu repositories, so install with Synaptic.

---

### Post by jason.b.c on 2008-10-26
> **jason.b.c said:**
> [http://ubuntuforums.org/showthread.php?t=396093](http://ubuntuforums.org/showthread.php?t=396093)

well i read through that whole entire thing , but it still dosen't tell me how to stealth my ports....

:confused:

---

### Post by p_quarles on 2008-10-26
> **jason.b.c said:**
> :confused:
If memory serves, iptables handles what you're calling "stealth" by setting the default policy to DROP (on input, output, and forward). Again, I don't use Firestarter (why? because hardware firewalls are better and it's a hell of a lot more trouble than it's worth), but that's what you're looking for.

---

### Post by jerome1232 on 2008-10-26
Well since iptables has been mentioned here are some guides about it for if you are interested.
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

ufw is a much simpler frontend to iptables
[https://wiki.ubuntu.com/UbuntuFirewall](https://wiki.ubuntu.com/UbuntuFirewall)

gufw is a graphical frontend to ufw
[http://gufw.tuxfamily.org/index.html](http://gufw.tuxfamily.org/index.html)

There only difference between having 'stealthed' ports and 'closed' ports is that it's harder to determine if you computer is actually online if the ports are 'stealthed'.
In iptables-speak - drop silently drops the packet
reject - drops the packet and sends the sender an error. Usually will show up as connection refused.

Some port scanners will also take longer to scan a computer that is stealthed as opposed to closed, it doesn't seem to slow nmap down for me.

And what good does knowing your machine is online do someone if all your ports are closed anyways?

I agree with p_quarles hardware firewalls are better, they are generally easier to configure, and malware can't turn them off. :) But that doesn't seem to be an option for you hence the guides.

---

### Post by ubromtoo on 2009-03-03
Jason.B.C :

     Open Firestarter, click on Preferences,then click on ICMP Filtering ,

then check the box "Enable ICMP filtering", and do not check any of the

boxes underneath .  Then click "accept" .

     It works for me !

---

### Post by dcstar on 2009-03-03
> **jerome1232 said:**
> 
.......
And what good does knowing your machine is online do someone if all your ports are closed anyways?
.......

Because then someone **knows** the IP address exists can can still hit you with a DOS attack safe in the knowledge that something exists there and their attack will have an effect, rather than have doubt when the ports do not respond at all.

And why is this ancient thread revived anyway?

---

