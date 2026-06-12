---
title: "Pidgin drops AIM chatrooms."
date: 2008-11-15
forum: General Help
---

### Post by spongypants23 on 2008-11-15
Hey guys, having a bit of a problem with Pidgin 2.5.2:

First off, I'm rarely able to join a chat room, be it with an invite or using the Join Chat feature. In the off chance that I do get into the chat room, I will be disconnected from the chat after about 15 minutes or so.

The following is from the debug output when I get disconnected:
```
(02:07:54) oscar: Scheduling destruction of FLAP connection of type 0x000e
(02:07:54) oscar: Destroying oscar connection of type 0x000e.  Disconnect reason is 4
(02:07:54) oscar: Disconnected.  Code is 0x0000 and msg is Connection dropped by partner.
(02:07:54) server: Leaving room: ###
```
In order to re-join the chat room I have to re-start Pidgin, and having to do this every 15 minutes gets annoying.

Anyone know a fix?

Is this correlated in any way to the current issues with the Intel 4965 wireless cards?

And just for reference, system information:
Dell XPS M1530
Wireless card: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron]
Ubuntu 8.04.1 Hardy Heron

---

### Post by RunLengthLimited on 2009-01-02
This happens to me in pidgin as well.  How did you get the debug trace?

---

### Post by spongypants23 on 2009-01-02
> **RunLengthLimited said:**
> This happens to me in pidgin as well.  How did you get the debug trace?

I ran Pidgin via the terminal. Debug info is printed as you use it.

---

### Post by RunLengthLimited on 2009-01-02
Hmmm.  Just tried it again.  No trace in the terminal it ran from before getting booted from chatroom.  Earlier in the session it had spit out:
```

(pidgin:9086): GStreamer-CRITICAL **: gst_element_set_state: assertion `GST_IS_ELEMENT (element)' failed

(pidgin:9086): GStreamer-CRITICAL **: gst_object_unref: assertion `((GObject *) object)->ref_count > 0' failed

(pidgin:9086): GStreamer-CRITICAL **: gst_element_set_state: assertion `GST_IS_ELEMENT (element)' failed

(pidgin:9086): GStreamer-CRITICAL **: gst_object_unref: assertion `((GObject *) object)->ref_count > 0' failed

(pidgin:9086): GStreamer-CRITICAL **: gst_element_set_state: assertion `GST_IS_ELEMENT (element)' failed

(pidgin:9086): GStreamer-CRITICAL **: gst_object_unref: assertion `((GObject *) object)->ref_count > 0' failed

```
but did not quit.  Sigh.

---

### Post by exploder on 2009-01-02
Try Pidgin 2.5.3a, there have been quite a few bug fixes. You can get it here.

[http://www.getdeb.net/search.php?keywords=pidgin](http://www.getdeb.net/search.php?keywords=pidgin)

I completely removed the old version using Synaptic, then installed the debs and put back the otr plugin that was removed. Pidgin works just fine here.

---

### Post by spongypants23 on 2009-01-02
> **exploder said:**
> Try Pidgin 2.5.3a, there have been quite a few bug fixes. You can get it here.

[http://www.getdeb.net/search.php?keywords=pidgin](http://www.getdeb.net/search.php?keywords=pidgin)

I completely removed the old version using Synaptic, then installed the debs and put back the otr plugin that was removed. Pidgin works just fine here.

Hmm, I'll be sure to give this a shot. I'll report back late tomorrow with my findings.

---

### Post by spongypants23 on 2009-01-03
Following up:

It seems that the problem persists in Pidgin 2.5.3. I am still unable to connect or create chat rooms, leading me to believe the dropping of chat rooms will still occur.

However, I do believe it is worth noting that this problem only starts occurring about 5-15 minutes after Pidgin has been running. I will run Pidgin for a little bit while outputting debug to a text file, and post any interesting finds. Maybe there's something there that will give a clue as to what is happening.



Also, RunLengthLimited:

My bad. I forgot to say that I ran pidgin with the -d option to enable debug output.


-------------

Follow up to follow up!

I have confirmed that the problem still exists. Here are the interesting tidbits from the debug log I have.

This is when I was kicked out of the chat room:
```
(19:44:53) oscar: Scheduling destruction of FLAP connection of type 0x000e
(19:44:53) oscar: Destroying oscar connection of type 0x000e.  Disconnect reason is 4
(19:44:53) oscar: Disconnected.  Code is 0x0000 and msg is Förbindelse borttagen av partnern
(19:44:53) server: Leaving room: chatlolimtestingstuff
```
"Förbindelse borttagen av partnern" roughly means that the connection was dropped by peer.


This is when I tried to re-create the chat room:
```
(19:45:13) oscar: Attempting to join chat room chatlolimtestingstuff.
(19:45:13) oscar: chatnav exists, creating room
```
However, it seems that no room is created, as no chat window pops up.

Other than those two sections, there's nothing that really sticks out. However if anyone is interested I can attach the entire log.

---

### Post by stefie10 on 2009-06-11
Hi,

I got it to work from the same machine by trying a different AIM account, on the same machine. I think it's some kind of rate limiting thing, because it happened after I had a flaky wireless connection and then switched to wired.   

Stefanie

---

