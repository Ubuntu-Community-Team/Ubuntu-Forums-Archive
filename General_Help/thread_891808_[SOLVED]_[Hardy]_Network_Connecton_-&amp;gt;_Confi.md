---
title: "[SOLVED] [Hardy] Network Connecton -&amp;gt; Configure -&amp;gt; &amp;quot;The interface does not exist&amp;quot;"
date: 2008-08-16
forum: General Help
---

### Post by Jack Waugh on 2008-08-16
I just upgraded my System 76 Pangolin to Hardy Heron from the previous long-term support (LTS) version of Ubuntu.  When I open the Network Connection icon (the one that shows the two computer screens that light up with network activity), then click the Configure button, then supply my password, a dialog box comes up saying "The interface does not exist" and "Check that it is correctly typed and that it is correctly supported by your system.".  This even though the wired Ethernet interface is working fine (I send this to you over it).  When I dismiss the dialog, I get no tool coming up to let me configure the network interfaces; it came up fine in the previous LTS.  I suppose this problem is not of the essence because I suppose I shall be able to configure the interfaces with "ifconfig" and friends.  But I wonder whether anybody has a correction for this failure.  Thanks in advance.

---

### Post by Jack Waugh on 2008-08-26
OK, there's a great workaround at [https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/184711/comments/23](https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/184711/comments/23) , namely, "run 'network-admin' directly as a non-root user without any options".  The window comes up with an "unlock" button.  You exercise that, supply your password (assuming you have sudo power), and then you can configure away.  Thanks are due to user "eryksun" over there on the defect-reporting site.

---

