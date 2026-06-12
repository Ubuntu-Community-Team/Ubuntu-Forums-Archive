---
title: "Bourne Shell Fork?"
date: 2008-12-01
forum: General Help
---

### Post by seanmu13 on 2008-12-01
Is there a way to fork off a process from a bourne shell?  I want to launch a GUI program and still be able to use the terminal from which it was launched.

Thanks,
seanmu13

---

### Post by lavinog on 2008-12-01
add a & to the end of the program name

ex:
```
gedit filename&
```
it will launch gedit for filename but leave your terminal available

---

### Post by seanmu13 on 2008-12-02
Thanks, that works but the "[username@computer]#" prompt does not come up, the cursor just sits there with a blank line.  You can still enter commands as usual, but is it at all possible for the prompt to reappear while the separately launched process is still running?

-Sean

---

### Post by lavinog on 2008-12-02
It might have something to do with the specific program you are running.
Sometimes pressing enter afterwards should give you a prompt.
What program are you running?

---

### Post by seanmu13 on 2008-12-02
> **lavinog said:**
> It might have something to do with the specific program you are running.
Sometimes pressing enter afterwards should give you a prompt.
What program are you running?

I am just running a simple Java GUI program.  Pressing enter does give me the prompt, thanks.

-Sean

---

### Post by adult swim on 2008-12-02
have you tried nohup?
```
nohup command
```
EDIT: woops i thought you wanted to be able to close the terminal, not continue using it.

---

