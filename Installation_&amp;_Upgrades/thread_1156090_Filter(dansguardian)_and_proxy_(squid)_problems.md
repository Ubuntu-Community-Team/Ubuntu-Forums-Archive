---
title: "Filter(dansguardian) and proxy (squid) problems"
date: 2009-05-11
forum: Installation &amp; Upgrades
---

### Post by slambro on 2009-05-11
[FONT=Calibri][SIZE=3]Hello Everybody[/SIZE][/FONT]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Im hoping you can help me out. This is my situation.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]On a Ubuntu 9.04 Server I have the following :[/SIZE][/FONT]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Server running Dansguardian and Squid then another  ubuntu 7.04 server acting as a parent proxy.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Danguardian.conf has the following (amongst others):[/SIZE][/FONT]
[FONT=Calibri][SIZE=3][COLOR=blue]Filterip =[/COLOR][/SIZE][/FONT]
[FONT=Calibri][SIZE=3][COLOR=blue]Filterport = 8080[/COLOR][/SIZE][/FONT]
[FONT=Calibri][SIZE=3][COLOR=blue]Proxyip = 127.0.0.1[/COLOR][/SIZE][/FONT]
[FONT=Calibri][SIZE=3][COLOR=blue]Proxyport = 3128[/COLOR][/SIZE][/FONT]
[FONT=Calibri][SIZE=3][COLOR=black][COLOR=#1f497d]forwardedfor = on[/COLOR]
[/COLOR][/SIZE][/FONT][FONT=Calibri][SIZE=3][COLOR=black][COLOR=#1f497d] u[/COLOR][COLOR=#1f497d]sexforwardedfor = off[/COLOR][/COLOR]
[COLOR=#1f497d] [/COLOR]
[COLOR=#1f497d][/COLOR][/SIZE][/FONT][FONT=Calibri][SIZE=3]Squid.conf has the following (amongst others) :[/SIZE][/FONT]
[FONT=Calibri][SIZE=3][COLOR=blue]http_port 3128[/COLOR][/SIZE][/FONT]
[FONT=Calibri][SIZE=3][COLOR=blue]cache_peer 192.168.100.1 parent 3128 0 proxy-only no-query[/COLOR][/SIZE][/FONT]
[COLOR=#1f497d][FONT=Calibri][COLOR=blue]forwarded_for on[/COLOR][/FONT][/COLOR]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]The clients web browser point to the ip of the server with port 8080.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3][/SIZE][/FONT] 
[FONT=Calibri][SIZE=3]The filtering is working (ie dansguardian) but proxying is bypassing the ACL’s of the first squid and going directly to the parent.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3][/SIZE][/FONT] 
[FONT=Calibri][SIZE=3]Have i overlooked something?  What iptables rules if any can I add to have dansguardian (8080) send to 3128 of the first squid server?[/SIZE][/FONT]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Make any sense?[/SIZE][/FONT]
Thanks in Advance 
S

---

