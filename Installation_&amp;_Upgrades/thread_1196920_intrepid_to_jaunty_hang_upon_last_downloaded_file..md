---
title: "intrepid to jaunty hang upon last downloaded file."
date: 2009-06-25
forum: Installation &amp; Upgrades
---

### Post by dragos240 on 2009-06-25
I was upgrading my intrepid box, and I noticed that on the 1491th file, which is the last one, just hung there for a while, I was thinking that it was just checking the file integrity of all of the files downloaded, but it downloaded in about 30 minutes, and it's been 2 hours now. It's still going. What should I do?

---

### Post by starcraft.man on 2009-06-25
> **dragos240 said:**
> I was upgrading my intrepid box, and I noticed that on the 1491th file, which is the last one, just hung there for a while, I was thinking that it was just checking the file integrity of all of the files downloaded, but it downloaded in about 30 minutes, and it's been 2 hours now. It's still going. What should I do?

Your machine didn't freeze eh? It just sits there, like a zombie in the update manager. Can you ping the server your set up to download from to check there's nothing wrong via that method? If you open the system monitor is there any up or down network traffic under resources tab?

Assuming that all works, I assume something happened and the update manager crashed, if so it should be evident from the processes tab, just check the status of the manager. If it did crash, you might just have to kill it, I mean if it's been zombied for 2 hours I don't think it'll magically start up again... unless maybe it was server issue but unlikely.

I'm uncertain from there (I clean install almost every time, separate home partition stores my configs), since you were only at the download phase I assume you didn't modify any files and you can just start it back up and it will keep going. I could be wrong, if it did start writing files ya may just be out of luck. Try the above first and get back to me on that, I'm afraid I've never had the few upgrades I've done go awry.

---

### Post by dragos240 on 2009-06-25
Actually nevermind..... I canceled the upgrade manager, and restarted it, I have jaunty now. Thank you.

---

### Post by starcraft.man on 2009-06-25
> **dragos240 said:**
> Actually nevermind..... I canceled the upgrade manager, and restarted it, I have jaunty now. Thank you.

No problem. Guess I wrote all that for naught, enjoy.

---

