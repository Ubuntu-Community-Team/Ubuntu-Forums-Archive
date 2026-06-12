---
title: "Firefox produces hiccups"
date: 2008-11-26
forum: General Help
---

### Post by Drakim on 2008-11-26
So, I was quite surprised at this problem.

It appears that, when I'm using Firefox, and I'm on a page that has JavaScript writing to a <canvas> element, then my whole system gets hiccups.

I tried 4-5 different pages that uses JavaScript and the <canvas>, and they all produce the same problem. Lastly, I tried making my own very very basic canvas demo, which did nothing but draw a circle at a reasonable interval, and I still get those hiccups.

It's really strange. The hiccups comes at intervals of about a second, but in between those seconds, it runs smoothly, despite JavaScript drawing several shapes to the canvas and clearing them. And yes, I tried slowing down how often I draw to the canvas, no effect.

I'm running Ubuntu 8.04 Hardy Heron, Mozilla Firefox 3.0.4 with no extensions.

---

### Post by Drakim on 2008-11-26
Nobody? This is quite a bothersome problem since I want to start making my own JavaScript things which uses <canvas>

Edit: Okay, I tested, and the hiccups doesn't appear in Firefox 2.

---

