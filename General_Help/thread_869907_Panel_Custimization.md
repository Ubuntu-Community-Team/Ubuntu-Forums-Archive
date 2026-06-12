---
title: "Panel Custimization"
date: 2008-07-25
forum: General Help
---

### Post by mman426 on 2008-07-25
Hey, this may be something simple that I am overlooking, but does anybody know how to get rid of those rectangles at the edges of the panel when you have it set not to expand. Here's a pic of my desktop to show you what I mean.

---

### Post by n6yga on 2008-07-25
Try right-clicking on the panel and de-select "Show Hide Buttons." I think that will fix your issue. That's how it works on my machines.

Mark.

---

### Post by Slug71 on 2008-07-25
Anyone know how i can get that rounded shiny look for my taskbar?
Also want to make my windows borders see-thru.
Sorry guys im a newbie and still have no idea what im doing.

---

### Post by overdrank on 2008-07-25
> **Slug71 said:**
> Anyone know how i can get that rounded shiny look for my taskbar?
Also want to make my windows borders see-thru.
Sorry guys im a newbie and still have no idea what im doing.

Take a look at the FAQ's at the top of the page in this forum or the link in my signature.

@ n6yga, I tried your suggestion but it does not remove the rectangles the OP what speaking of. I have tried others ways also and no luck.

---

### Post by mman426 on 2008-07-25
I already have the panel set to not show the hide buttons. Thanks anyway though. Now that I think about it I could just go back to the expanded panel and move everything to one side. The only problem is I probably won't be able to put conky in the corner like I want to.

---

### Post by mc4100 on 2008-07-25
> **mman426 said:**
> I already have the panel set to not show the hide buttons. Thanks anyway though. Now that I think about it I could just go back to the expanded panel and move everything to one side. The only problem is I probably won't be able to put conky in the corner like I want to.

You can still have conky in the corner, just set a bigger "y" gap in ~/.conkyrc, so that it's not being overlapped by the panel:

gap_x 8
gap_y 34

---

### Post by steveneddy on 2008-07-26
> **mc4100 said:**
> You can still have conky in the corner, just set a bigger "y" gap in ~/.conkyrc, so that it's not being overlapped by the panel:

gap_x 8
gap_y 34

I agree - expand the panel and position conky a little lower.

---

### Post by n6yga on 2008-07-26
> **overdrank said:**
> Take a look at the FAQ's at the top of the page in this forum or the link in my signature.

@ n6yga, I tried your suggestion but it does not remove the rectangles the OP what speaking of. I have tried others ways also and no luck.

Ah. You, of course, are right. Those are the Grippers. When you have a panel set to not-expand you get the grippers. Sorry, I thought the OP wanted to just remove the arrows. Short of crating a theme with invisible Grippers I'm not sure there is a way.

Mark.

---

