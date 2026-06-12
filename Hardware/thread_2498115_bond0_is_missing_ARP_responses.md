---
title: "bond0 is missing ARP responses"
date: 2024-05-31
forum: Hardware
---

### Post by tony-sarajarvi on 2024-05-31
This problem of ours is also posted on Dell's forum: [https://www.dell.com/community/en/conversations/poweredge-hardware-general/possible-bcm57504-problems/66583f6707734669487e8f77](https://www.dell.com/community/en/conversations/poweredge-hardware-general/possible-bcm57504-problems/66583f6707734669487e8f77)
But as suggested there, and frankly the problem might be on the distro side, we're throwing our nets here as well in hope of help.

[COLOR=#0A0A14][FONT=-apple-system]Concerning Dell R650 servers with BCM57504. Our setup has Ubuntu 22.04 or 24.04 running. 2 interfaces eno12399np0 and eno12409np1 are bonded together to bond0.[/FONT][/COLOR]
[COLOR=#0A0A14][FONT=-apple-system]
We are using the server as an OpenNebula build server, where OpenNebula creates a bridge br0 whenever it launches a KVM VM on the server. If the last VM is deleted, br0 is also removed. The VMs will receive their own virtual NIC, e.g. one-300234-0 that connects to br0 and traffic is vlan tagged. It also creates a virtual nic bond0.123@bond0 which I guess does the vlan tagging for the VMs and br0 gets bond0.123 as an interface.[/FONT][/COLOR]
[COLOR=#0A0A14][FONT=-apple-system]
Now the weirdest things happen randomly. Sometimes we end up with a virtual machine who couldn't connect to another VM within the same network cluster. It's an sccache server running in another VM on another host, so I'll refer to it as sccache VM so you don't get lost here. And by connect I mean ssh, ping you name it. But just this one! This problematic VM could connect to any other VM we've tried within the same network segment at the same time. And those could once again connect to this sccache VM which is unreachable for this problematic VM.[/FONT][/COLOR]
[COLOR=#0A0A14][FONT=-apple-system]
When we dug deeper into the issue, we found out that our problematic VM never received the ARP reply, when it asked who 192.x.x.x was. We confirmed that the sccache VM did reply to it, and we could tshark the reply, but this VM never received it. Next thing we did was that we went outside the VM and went to the host OS and tsharked the br0 and bond0. Neither of those saw the ARP response. As if the reply never got to the server at all. But if the sccache VM pings for the problematic VM and ARP requests for the MAC address, the problematic VM does get the broadcast and sends a reply that is received by sccache VM. So the line partially works between them. Only the ARP responses from sccache VM to the problematic VM one are lost somewhere within the problematic host. Or in other words, broadcasts are received by the problematic VM, but not unicasts, when sent from sccache VM.[/FONT][/COLOR]
[COLOR=#0A0A14][FONT=-apple-system]
So we took another similar Dell server to help us out here. We did a port mirroring setup on the switch, so that both servers receive the same IP packages.[/FONT][/COLOR]
[COLOR=#0A0A14][FONT=-apple-system]
What happened now was that while the first server never receives the ARP reply, the second one got it. This was confirmed by tsharking the bond0 on both servers. So it starts looking like a firmware or hardware bug on the NIC side.[/FONT][/COLOR]
[COLOR=#0A0A14][FONT=-apple-system]
There is yet another very weird thing here, which we can't explain.[/FONT][/COLOR]
[COLOR=#0A0A14][FONT=-apple-system]
While the ARP reply is never received on either the host or the VM, the ARP table in the VM actually gets filled with the correct ARP response. Where does that come from? How can it receive the ARP reply without ever getting the response? And if it really got the ARP information, why is ping still stuck? stracing ping ends up in a loop printing out "EAGAIN (Resource temporary unavailable)" whatever that means. And once again, if I ping something else in the same segment, it works. And ARP replies are visible.[/FONT][/COLOR]
[COLOR=#0A0A14][FONT=-apple-system]
If we go ahead and delete this VM, the br0 gets deleted as well. If we now re-create a VM the br0 will be created again and most likely everything will work again. But just most likely. It's a game of dice here.[/FONT][/COLOR]
[COLOR=#0A0A14][FONT=-apple-system]
We've also end up in a situations where br0 never gets linked to bond0.123. Once again, a random situation while running the same tools and scripts. When this happens, the VMs that use br0 they naturally don't have any kind of network connection. How can br0 be left out of an interface its instructed to have?
[/FONT][/COLOR]
[COLOR=#0A0A14][FONT=-apple-system]What's the next thing we could try out and debug? [/FONT][/COLOR]

---

### Post by currentshaft on 2024-05-31
To me it sounds like either a race condition in some bootstrap script OR a duplicate MAC/IP assigned on the network. Are you able to check those out or share any relevant bits?

---

### Post by tony-sarajarvi on 2024-06-03
A duplicate MAC/IP is doubtful, since the main problem gets fixed by just recreating the VMs which recreates br0. And as ARP replies start coming through after a recreation of br0, i'm starting to point my finger at that direction. A race condition is likely i'd say...somewhere within bridge creations. But that still doesn't tell us why broadcasts are received, but unicasts not. Or is there some internal state machine within the network stack so that it doesn't empty some unicast buffer or smt in my case.

---

