---
title: "Synergy freezing and locking up temporarily"
date: 2008-08-11
forum: General Help
---

### Post by kooldino on 2008-08-11
Hi all, I basically have [this]("http://ubuntuforums.org/showthread.php?t=761854&highlight=synergy+freeze") problem, except I'm running the server on my linux machine, not the client.

Basically, I run a synergy server on my Kubuntu 7.10 box and the client on my XP Pro machine. It used to work very well, but out of nowhere, it started flaking out on me the past few weeks. Frequently and randomly, the mouse & keyboard seem to freeze completely, but keyboard input gets through eventually, without any lost keystrokes.

I'm running the latest versions of Synergy on both.

I tried running the server as root, but it doesn't seem to be helping.

---

### Post by kooldino on 2008-08-11
Changing the Nice did squat as well.

---

### Post by kooldino on 2008-08-12
This is driving me up a wall...I can't accomplish anything like this.

I tried swapping the roles of the machine so that the server ran on windows and the client was on linux (client running as root) and it still has the same issue.

---

### Post by kooldino on 2008-08-13
$10 paypal reward to anyone who can solve my issue.

---

### Post by kooldino on 2008-08-14
bump - anyone?

---

### Post by kooldino on 2008-08-18
Someone please help me...

---

### Post by kooldino on 2008-08-21
$30 via paypal to whoever can fix this issue...

---

### Post by moloth on 2008-09-24
Could be a firewall issue dropping some packets. Install any antivirus / firewall packages on windows?

---

### Post by tx413 on 2008-12-04
Well "nice" worked for me.  I had the exact same problem today.  I'm running a live slax distro on my normally RedHat box, and synergy was freezing just like you said.  The synergy server is on Win XP with the client on Slax.

A quick peek with wireshark showed that the network packets were making it back and forth just fine.  So I tried running synergyc on the Slax side with "nice -n -5" and all my freezes went away.

Hope that helps someone.

---

### Post by MarcDurant on 2009-01-16
I was having the same intermittent freeze issue running the synergy server on OSX 10.4 and the client on Fedora 9.

At first running the client with "nice" wasn't helping, but then I remembered that I had it set up to connect via an ssh tunnel to the server.  Running with nice and connecting directly to the server solved the problem.  I haven't tried running the ssh tunnel command with nice, but I'll do that now.

Hope that helps.

---

### Post by MarcDurant on 2009-01-16
I'm wrong - the freezes come less often but last just as long.  Probably 2 seconds of freezing every 10-15 seconds.  I can make it much worse by loading a webpage or putting out a lot of network traffic, but I would not expect freezes of that length to be caused by simple network latency.

Back to the drawing board.

---

### Post by MarcDurant on 2009-01-19
Fixed it with this patch:
[http://sourceforge.net/tracker/?func=detail&atid=490469&aid=2141567&group_id=59275](http://sourceforge.net/tracker/?func=detail&atid=490469&aid=2141567&group_id=59275)

---

### Post by kooldino on 2009-01-22
> **MarcDurant said:**
> Fixed it with this patch:
[http://sourceforge.net/tracker/?func=detail&atid=490469&aid=2141567&group_id=59275](http://sourceforge.net/tracker/?func=detail&atid=490469&aid=2141567&group_id=59275)

Very nice, good find.

I had forgotten about this issue...I eventually figured it out and forgot to post the solution.  For me, it was a new network switch.  Apparently the one I had was glitchy.  Odd, eh?

---

### Post by Tomatz on 2009-01-22
Post the output of the command **top** when it happens.

---

### Post by kooldino on 2009-01-22
> **Tomatz said:**
> Post the output of the command **top** when it happens.

or better yet, pgrep synergy

---

### Post by cooper6581 on 2009-01-27
> **MarcDurant said:**
> Fixed it with this patch:
[http://sourceforge.net/tracker/?func=detail&atid=490469&aid=2141567&group_id=59275](http://sourceforge.net/tracker/?func=detail&atid=490469&aid=2141567&group_id=59275)

Worked perfect for me!  Thanks so much!

---

### Post by dth4h on 2011-08-25
I am having a problem with Synergy freezing up too.  Windows 7 is the server with Fedora 15 client.  I saw that you guys said this patch fixed the freezing problem but when I go here:

[http://sourceforge.net/tracker/?func=detail&atid=490469&aid=2141567&group_id=59275](http://sourceforge.net/tracker/?func=detail&atid=490469&aid=2141567&group_id=59275)

It says this:
ERROR 
Artifact: This Artifact Has Been Made Private. Only Group Members Can View Private ArtifactTypes.

Is there anywhere else I can get the patch from?

---

