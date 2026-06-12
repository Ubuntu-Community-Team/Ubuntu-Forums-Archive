---
title: "[SOLVED] SSH Hangs"
date: 2008-11-17
forum: General Help
---

### Post by AusIV4 on 2008-11-17
I just upgraded my laptop to Intrepid, and I've run into a bit of an odd problem.

When I try to SSH in from another computer, it acknowledges credentials, then hangs. Running top on my laptop reveals that there is a process called "-bash" that is running at 100% cpu. Killing this process completes the SSH login process, and I get a usable command line.

This is a viable option when I'm at my laptop and need to move some files to another computer, but if I need to SSH to my laptop remotely, it just hangs indefinitely (presumably running up my CPU as well).

Does anyone know how to fix this?

---

### Post by iponeverything on 2008-11-17
Try adding the originating machine to the /etc/hosts on the destination machine.

---

### Post by AusIV4 on 2008-11-17
Recreating my .bashrc solved the problem. I don't know what was going on. Seems to be fixed now. Marking as solved.

---

