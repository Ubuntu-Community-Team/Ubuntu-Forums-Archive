---
title: "Concern about Recovery Mode"
date: 2005-11-30
forum: General Help
---

### Post by invalid on 2005-11-30
Hi,
 
I recently had to boot into the "Recovery Mode" to edit a bad file, and it got me thinking about concern for security. What is to prevent someone with local access from booting the machine into this mode, and doing what they please as a root user? It seems a little unsafe from my point of view. 

I am quite interested in reading feedback regarding this.

Cb

---

### Post by Xian on 2005-11-30
You can create a root password (search the forum) that will have to be given if you boot in recovery mode, but the simple truth is that if someone has access to your machine they already can get anything they want.

---

### Post by RAOF on 2005-11-30
Yes, if you're concerned about local-access security you'll need to have a GRUB password, and a bios password, and have the computer set to boot only from the harddrive, and probably a whole bunch of other stuff.

But indeed, if they have physical access to the system they can just grab the harddrive, and (unless you've encryped everything on there) get what they want from that.

---

