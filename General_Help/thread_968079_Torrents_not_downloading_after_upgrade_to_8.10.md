---
title: "Torrents not downloading after upgrade to 8.10"
date: 2008-11-02
forum: General Help
---

### Post by Codename46 on 2008-11-02
Hey guys,

I just upgraded to 8.10 and noticed that none of my torrents (I use Vuze) are downloading or are downloading EXTREMELY slow, even though it says the tracker is online and there are plenty of seeds/leechers.

I know it's not the problem with my router because everything used to work fine in 8.04 and I didn't change any configuration in my router.

When I run the Nat/Firewall test it says it's OK, but when I try running the "Speed Test" it gives me this error:

"Test failed: Test aborted: Scheduling of the test failed: Server failed. Error: Verification failed, SpeedTest request handler failed"

I tried redownloading one of my older torrents that still has a healthy seed/leech that I was able to download with good speeds before, and it won't start.

Help?

---

### Post by Jarz Corp on 2008-11-02
Just wanted to say ditto, and then I wanted to p.s and moan about yet another Ubuntu upgrade that brings more problems then bug-fixes.

---

### Post by Codename46 on 2008-11-02
> **Jarz Corp said:**
> Just wanted to say ditto, and then I wanted to p.s and moan about yet another Ubuntu upgrade that brings more problems then bug-fixes.

Well the good news is that i narrowed down the problem to exclusively Vuze. I tried torrenting with a different client (Transmission) and that works. I dunno if it's a problem with Vuze or the Java client.

---

### Post by fletchoid on 2008-11-02
Used Azureus just fine until I upgraded to 8.10    Then, azureus broken.  So, installed again, still broken.  Spent 2 hours reinstalling java, azureus, etc.  Finally got Vuze to install, but NOW can't get torrents to automatically open with Vuze.  This is starting to seem like a Vista session.  Round and Round and not going anywhere.  Has anyone figured out how to get Vuze or Azureus to be the default torrent handler?? I am sure MANY people are having this same problem.  Help!?!?!?

---

### Post by fullmetalgerbil on 2008-11-02
If you uninstall all other Bit Torrent clients (like Transmission) then Azureus will become default. At least thats been the fix in my experience wih BT and Ubuntu. Seems there is a conflict between Ubuntu 8.10 and Azureus/Vuze though. If you're looking for a better BT client anyways, try Deluge. I've found it to be faster and better on resources than Azureus.

---

