---
title: "No ping reply between two interfaces in same machine"
date: 2008-11-07
forum: General Help
---

### Post by maxim99 on 2008-11-07
I've got an odd situation.

I have a machine with two NICs on board. I have set up one at IP 192.168.1.1, the other at 192.168.1.2.

I have a third machine which as windows on it and it's set up at 192.168.1.3, just one interface.

All three interfaces are plugged into a switch.

I'm able to ping from 192.168.1.3 to both 1 and 2, no issues, I receive a reply as expected.

I'm able to ping from both 1, and 2, to 3. Everything works.

However, I don't receive a reply when I ping from 1 to 2. I did a tcpdump and received messaging says that the echo request was made, but no reply is sent.

Ping (using -I to specify the interface to ping from) returns a "Destination Host Unreachable."

Is this possible? Is it a hardware thing? Maybe a software with the ping program?

It seems odd, I should be able to do this, right?

---

### Post by maxim99 on 2008-12-04
If found that it's a common issue when attempting to run two interfaces in the same machine and having them both be on the same subnet.

---

### Post by sedawk on 2008-12-04
I think the problem is with the routing, e.g. the unexpected ways
a system can choose to send the (reply) package.

I think you can "force" ping (and other tools) to use a dedicated
interface instead of the default logic.
Also routing can be bound to an interface.

I have a few servers with multiple (multi-port) cards and
more than one IP per port (eth0, eth0:1, etch0:2).
This can be very "entertaining" if something gets "out of sync".

---

