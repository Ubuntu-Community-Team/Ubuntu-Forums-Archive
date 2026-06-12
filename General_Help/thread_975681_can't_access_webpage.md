---
title: "can't access webpage"
date: 2008-11-08
forum: General Help
---

### Post by rick08 on 2008-11-08
I go to a vocational school that uses cisco networking academy curriculum.  I tried to log onto the cisco.netacad.net website and it just comes up with a blank webpage.  I tried using firefox, seamonkey, epiphany, and opera and none of them worked.  I really need to log on this weekend to take a test so any help is appreciated.  I know at school we have to use Internet destroyer at school to access the curriculum, but there has to be some way to access the curriculum using another web browser.

---

### Post by knutschr on 2008-11-08
You could try installing IE through WINE

---

### Post by rick08 on 2008-11-08
i really don't want to do that.  That might be very painful.  I would prefer some other option.

---

### Post by ju2wheels on 2008-11-08
1. You said you were having issues logging in, so I assume you have access to the internet in general and can access other sites so thats not a problem?

2. Do you know if their site uses anything like flash or java plugins? Do you have java (and the java plugin) and flash installed if they are needed?

3. If 2 does not apply, just to rule out that they arent just checking the browser type, try this Firefox plugin: [https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

---

### Post by knutschr on 2008-11-08
Then try konqueror

---

### Post by rick08 on 2008-11-08
I tried step 3 since I have java and flash and all that stuff good.  User Agent switcher still does not do anything for me.

---

### Post by soro2005 on 2008-11-08
- You may have cookies disabled (improbable that this is the problem if you say it doesn't work in any of the browsers)

- If the site has a Active X component, then you have to use IE. There is no emulation for this technology, and it's not implemented anywhere else.

- You may be required to log in through your school's proxy server. Are there any instructions on how to connect from home? You may want to make a test run with IE, if simply to exclude that that's the problem.

---

### Post by jamesstansell on 2008-11-08
Rick,

How blank is the page?  Do a view -> page source to see what the browser is actually getting.

What does someone need to do to reproduce the problem?  Start by giving the URL, then explain what steps you took.

Regards,

-james.

---

### Post by macuser9214 on 2008-11-08
I can confirm the same problem. The source of the blank page reveals a flash detection... I've been having flash problems with 'buntu, so I'm guessing this related...A bit annoying - since flash is getting more common on the web (as much as I dislike that fact, it's coming true), and it should be supported out of the box. Disappointing.

---

### Post by macuser9214 on 2008-11-08
Wow - looks like I might be going back to arch..or another distro.. this sucks.

---

