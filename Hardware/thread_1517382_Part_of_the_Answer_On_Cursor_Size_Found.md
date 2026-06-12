---
title: "Part of the Answer On Cursor Size Found"
date: 2010-06-25
forum: Hardware
---

### Post by oldefoxx on 2010-06-25
I have a notebook, which has the same problem as my Desktop with the 22" wide screen.  That is, at high resolution on either, the mouse cursor is almost invisible.  I will add that as I try to find it by moving it around, it can get smaller, or it can actually quit showing up altogether.  I can press the right mouse button, which lets me know where the mouse is in general, and sometimes I can then see it as being slightly larger, for a bit, but moving it about can make it smaller or cause it to disappear again.  When the cursor is over a text field, like the area where I am writing this, it becomes a tall but skinny I, and shifts back to the arrow shape when moved elsewhere.  I've reported this previously, but it has gone unanswered.

I had to get something done, so I went into the Package Manager under System/Administration to see what I could find with a search under cursor.  I found several packages, even one named big-cursor.  Most related to X11, so I also searched under X11.  Then I would add and remove packages in different sequences, to see what impact they might
have.  The cursor never changed from what it had been before.  Any instructions I found went back to earlier releases of Ubuntu, and were not consistent with how Ubuntu is now.  So I was still missing something. A couple of posts indicated that the placement was likely under System/Preferences someplace. So I started walking the whole menu tree structure to see what I could find.  I found nothing to help even though a new entry named Cursor Selection had been added.  It did offer choices, and a range of sizes, but selecting these did nothing.  In fact you have a button to go to a Theme Folder, but it does not work.  It seems to serve no purpose.

Checking some more posts, one gave me it might be tied in with System/Preferences/Appearance somehow.  But though it first looked promising, it seemed a dead end after going through the tabs underneath.  My final effort was to see what would happen if I picked a different theme.  And that is what finally did it.  Not the themes themselves, but the middle button underneath marked "Customize...".  That takes you to another Tabbed Menu, and the rightmost button is marked "Pointer".  You click on that, and you have a choice of pointer themes again, and you can choose this time, and below that list, there is a tiny slide bar labelled Size, and marked from small to large.

But, unfortunately, this is only half the puzzle.  You see, the only pointers that this will effect were displayed at the bottom of the window when the Cursor Selection choice was made.  None of the other
mouse pointers are impacted, so the little white arrow remains just small or even smaller.  And if you adjust the size bar, you do not see any effect on the mouse pointer, until you leave and go somewhere else and do something to cause the pointer to change to one of the ones that was impacted by the adjustment.  So how big or small do you want the pointer?  I guess you can play with it until you are happy with the results.

I missed it somewhere as I went back and forth on this, but there is a package in there that says it will get your real Windows mouse pointers and bring them over under Ubuntu if you want.  And it seems that you should also be able to get some new cursor themes off the internet to add to the collection on your PC.

Anyway, this seems to be one of those things where you can say that Ubuntu is getting there, but it is not there yet.  I just wonder how a different sized and shaped pointer will impact Ubuntu's notion of where the exact tip point is positioned?  Are we going to be like riflemen who have to aim off center to allow for the effects of windage and gravity?

At least a bit of progress today.

---

