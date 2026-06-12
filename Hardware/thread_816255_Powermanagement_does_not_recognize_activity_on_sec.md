---
title: "Powermanagement does not recognize activity on second screen"
date: 2008-06-02
forum: Hardware
---

### Post by scotty64 on 2008-06-02
I notice that the powermanagement on my Ubuntu laptop (Hardy on a Dell XPS M1330 with Nvidia graphicscard and drivers installed via envy) is not recognizing activity on the second screen. When I am working on that screen only, the powermanagement starts dimming it after the set interval of 15 minutes even when the cursor is active. The displays can only be reactivated by moving the cursor back to the (primary) laptop screen.
Can this be solved and how ?

---

### Post by scotty64 on 2008-06-18
> **scotty64 said:**
> I notice that the powermanagement on my Ubuntu laptop (Hardy on a Dell XPS M1330 with Nvidia graphicscard and drivers installed via envy) is not recognizing activity on the second screen. When I am working on that screen only, the powermanagement starts dimming it after the set interval of 15 minutes even when the cursor is active. The displays can only be reactivated by moving the cursor back to the (primary) laptop screen.
Can this be solved and how ?

The problem seems to be solved with my new setup: external TFT wired to the laptop via DVI / HDMI and xinerama enabled. My guess is that xinerama actually solved it as both screens are seen as one now. My former setup had them as two separate X-displays.

---

