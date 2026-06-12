---
title: "using standby"
date: 2005-06-29
forum: Hardware &amp; Laptops
---

### Post by byen on 2005-06-29
hey guys,
Though I am now a complete ubuntu convert and have been using ubuntu for over 2 months. There is a problem that i have which, if dealt, would help me a lot.

I try using the stanby option but it just does not seem to work. The system seems to go to standby but when I press the power button to turn-back on it just shuts down.Can someone please tell me the proper way to set my notebook up to get this workin.
Thank you fellas.
Byen

PS: have a Compaq presario amd 2800 with Ati radeon U1 graphic card if that matters.

---

### Post by nocturn on 2005-06-29
[QUOTE=byen]
PS: have a Compaq presario amd 2800 with Ati radeon U1 graphic card if that matters.[/QUOTE]

I have read that notebooks with ATI cards have problems going in power saving.

---

### Post by byen on 2005-06-29
[QUOTE=nocturn]I have read that notebooks with ATI cards have problems going in power saving.[/QUOTE]
 whoa. really. uh! well is it only on ubuntu ? it worked pretty well with fedora and sure did in windows... so is there anyway i can tweak it to run?
thank you 4 the reply.

---

### Post by nocturn on 2005-06-29
[QUOTE=byen]whoa. really. uh! well is it only on ubuntu ? it worked pretty well with fedora and sure did in windows... so is there anyway i can tweak it to run?
thank you 4 the reply.[/QUOTE]

I'm not sure about it (just something in the back of my mind).
I also think you need to modify /etc/default/acpi-support.

---

### Post by DHLawrence on 2005-07-01
How do you edit that file? I'm a newbie to Linux and don't know much about editing files.

---

### Post by flyinglizard on 2005-07-01
Open a terminal:  Applications -> System Tools -> Terminal.  Then at the terminal window type:

sudo gedit

you will be prompted for your password.

---

### Post by byen on 2005-07-01
[QUOTE=nocturn]I'm not sure about it (just something in the back of my mind).
I also think you need to modify /etc/default/acpi-support.[/QUOTE]
 how can i modify the said file? is there anyone who can give me a walkthrough?

thank you for your time fellas.

---

