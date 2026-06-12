---
title: "gwibber error."
date: 2008-12-02
forum: General Help
---

### Post by kimme on 2008-12-02
Help. My gwibber application is showing nothing in the main window, and when I start the gwibber application from the terminal it displays these error codes...

error: 0 is wrong flag id

How do I fix this problem?

---

### Post by ExpatPaul on 2008-12-02
I'm seeing the same issue - Gwibber isn't displaying anything. I don't see any error messages whe I start it from the terminal, though.


**Edit**: This has also been logged on Launchpad, along with a possible solution (remove and reinstall). I'm not in a position to try this right now but will do so later and let you know how I get on

Full details are here: [https://bugs.launchpad.net/gwibber/+bug/304033](https://bugs.launchpad.net/gwibber/+bug/304033)

---

### Post by ExpatPaul on 2008-12-02
Quck update...

I've dug around a bit, removed stuff, reinstalled stuff and repeated the process a couple of times. I'm running Hardy and it looks like Gwibber has been broken by the libwebkit-1.0-1 upgrade that I installed yesterday.

I am now at libwebkit-1.0-1 1.0.1-4+r38850~hardyppa2 and, according to Synaptic, no previous version is available.

Does anyone know if there is anywhere I can get hold of libwebkit-1.0-1 1.0.1-4+r38688~hardyppa1?

Thanks

---

