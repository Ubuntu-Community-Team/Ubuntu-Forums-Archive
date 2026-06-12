---
title: "Text in GIMP"
date: 2004-12-24
forum: General Help
---

### Post by monkeyshaman on 2004-12-24
Here's one I'll bet no one has asked before...

A fellow co-worker and I were playing with GIMP the other day and we were wondering if there is a way (other than through script-fu) to apply a gradient or other image to text?  In Adobe Photoshop it's relatively easy to do.  I was hoping someone on this forum might have the answer? ;)

Have a happy holiday everyone!

Arnold

---

### Post by ari on 2005-01-02
Yes. Create the text layer, then make sure the layer's "Preserve Transparency" box is set (it's to the right of Mode in the Layers dialog), then use the Gradient/Blend tool to apply the gradient to that layer. Voila, the gradient will only come out on the text itself.

---

### Post by Quest-Master on 2005-01-02
[QUOTE=ari]Yes. Create the text layer, then make sure the layer's "Preserve Transparency" box is set (it's to the right of Mode in the Layers dialog), then use the Gradient/Blend tool to apply the gradient to that layer. Voila, the gradient will only come out on the text itself.[/QUOTE]
 *off-topic*

Is it possible to add a border to text? Or add "stroke" as it is called in Photoshop and Paintshop Pro?

---

### Post by ari on 2005-01-02
[QUOTE=Quest-Master]*off-topic*

Is it possible to add a border to text? Or add "stroke" as it is called in Photoshop and Paintshop Pro?[/QUOTE]

Well, there are a few ways to do that.. one is to use the "Create path from text" button in the Text Tool options, then going to the Paths dialog and stroking the path into a new layer behind the text layer.
There's also Script-Fu->Decor->Fuzzy Border, and there's at least one other script that does a similar thing that I can't recall the name of at the moment.

---

### Post by monkeyshaman on 2005-01-03
[QUOTE=ari]Yes. Create the text layer, then make sure the layer's "Preserve Transparency" box is set (it's to the right of Mode in the Layers dialog), then use the Gradient/Blend tool to apply the gradient to that layer. Voila, the gradient will only come out on the text itself.[/QUOTE]

 Thanks for the great tips! :)

Arnold

---

### Post by Quest-Master on 2005-01-03
[QUOTE=monkeyshaman]Thanks for the great tips! :)

Arnold[/QUOTE]
 I can't get the stroke working ><

Is there a simple script just to simply add a border to the selected text?

---

### Post by ari on 2005-01-04
[QUOTE=Quest-Master]I can't get the stroke working ><

Is there a simple script just to simply add a border to the selected text?[/QUOTE]

Uh, did you actually read my reply?

---

### Post by Quest-Master on 2005-01-04
Yeah. And I couldn't get it working as I'd like it to, just as it said in the post..

---

### Post by wulf on 2005-01-05
Could you post an illustration of what you're trying to achieve, for example, a website that shows the kind of finished text you're after?

Wulf

---

