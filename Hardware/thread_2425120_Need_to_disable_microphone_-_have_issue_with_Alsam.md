---
title: "Need to disable microphone - have issue with Alsamixer"
date: 2019-08-20
forum: Hardware
---

### Post by setonic on 2019-08-20
I don't have an option to mute mic in alsamixer: see screenshot...

Why?

---

### Post by him610 on 2019-08-20
Welcome to the forums, setonic

How about providing more information about your system? Please show results, between code tags, of *inxi -Fz*

---

### Post by Yellow Pasque on 2019-08-21
Try hitting F5 to show input controls as well as output controls.

---

### Post by setonic on 2019-08-22
> **Yellow Pasque said:**
> Try hitting F5 to show input controls as well as output controls.

After I pressed F5 button I got this (see screenshot in attachment). Still can't see microphone.

---

### Post by Yellow Pasque on 2019-08-22
"Capture" would be the microphone volume. In this case, you are looking at pulseaudio (upper-level) volume controls. If you want to see the low-level controls for your specific card, then you need to press F6 and select your actual sound card.

---

### Post by setonic on 2019-08-22
> **Yellow Pasque said:**
> "Capture" would be the microphone volume. In this case, you are looking at pulseaudio (upper-level) volume controls. If you want to see the low-level controls for your specific card, then you need to press F6 and select your actual sound card.

Wow, looks like you are right: pressed F6 and chose HDA Intel PCH and there presents Mic Boost.

So, just to be sure, "Mic Boost" is my microphone?

---

### Post by Yellow Pasque on 2019-08-22
> **setonic said:**
> So, just to be sure, "Mic Boost" is my microphone?

No. Once again, you need to press F4 to display the input controls (or F5 to display both output and input controls).

---

### Post by setonic on 2019-08-22
Ok. How do you know that "Capture" is a microphone volume? What does mean "L" and "R"?

---

