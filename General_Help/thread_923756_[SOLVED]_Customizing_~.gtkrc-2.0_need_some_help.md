---
title: "[SOLVED] Customizing ~/.gtkrc-2.0 need some help"
date: 2008-09-18
forum: General Help
---

### Post by whitethorn on 2008-09-18
I have a dark theme installed (SlicknessBlack), I'm trying to get Bluefish (also got gedit to have a white background) to display the colors properly.  So far I've added this to my 
.gtkrc-2.0

> style "EditorStyle" {
        base[NORMAL]="#eeeeee"
        text[NORMAL]="#000000"
}
class "GtkTextView" style "EditorStyle"

Now I get a nice white background and black text.  The only problem I have at the moment is that the text marker, So pretty much the  | which blinks and shows you where you're about to type is a pale grey, I can't really tell where I'm gonna start typing.  Does ne1 know what I should put into above to get it to be black as well? I've done some searching but I dont' really know what it's called.


Ok I found out what I needed.   I needed to change the cursor-color.  This is my new .gtkrc-2.0

> style "EditorStyle" {
        base[NORMAL]="#eeeeee"
        text[NORMAL]="#000000"
        GtkTextView::cursor-color = "black"
        GtkEntry::cursor-color = "black"
}
class "GtkTextView" style "EditorStyle"

---

