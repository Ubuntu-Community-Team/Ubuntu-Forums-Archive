---
title: "vi copy/paste remaining part of sentence"
date: 2008-11-12
forum: General Help
---

### Post by cjjoy1980 on 2008-11-12
I am still getting used to using vi editor.  I am familiar with yank command and copy word (yw) commands.. but is there any key combination that copies the remaining of the sentence from the current cursor position?
i.e in the below sentence assuming that my cursor position is at end of welcome..how do I copy and paste the remaining words in italics("to world of computers")

for example: hello welcome [COLOR="RoyalBlue"]***to world of computers***[/COLOR]
                     
                  
thanks,
joy

---

### Post by ciscosurfer on 2008-11-12
In your example, you could do [COLOR=Red]4yw[/COLOR] (yank four words forward) or [COLOR=Red]y$[/COLOR] (yank until the end of the line).

---

### Post by cjjoy1980 on 2008-11-12
Thanks I was looking for the second option y$.  I will map that function to some single key so I can use only one key...

---

