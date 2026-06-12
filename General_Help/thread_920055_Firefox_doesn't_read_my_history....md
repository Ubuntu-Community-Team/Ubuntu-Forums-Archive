---
title: "Firefox doesn't read my history..."
date: 2008-09-14
forum: General Help
---

### Post by killerclick on 2008-09-14
I ran 'sudo firefox' once and since then Firefox isn't reading my history and shows a blank page instead of my home page. I can't see anything wrong with the .mozilla directory. How do I fix this without reinstalling Firefox?

---

### Post by killerclick on 2008-09-14
Uh, never mind, fixed it.
There is a directory in my user's home
.mozilla/firefox/5vioi5c4.default that had some files and folders that were owned by root so I changed them back...

---

### Post by Tanker Bob on 2008-09-14
You've probably already realized this, but you shouldn't use sudo to start apps that don't require it. Besides the security risks, it causes permission problems like you experienced.

---

### Post by killerclick on 2008-09-14
> **Tanker Bob said:**
> You've probably already realized this, but you shouldn't use sudo to start apps that don't require it. Besides the security risks, it causes permission problems like you experienced.

I was trying to fix the problem of no audio in Flash player and one of the solutions was to run Firefox as root... which only made things worse. Now I've fixed both problems with the help from the forums and a little tinkering.

---

### Post by Tanker Bob on 2008-09-14
Glad that you're up and running!

---

