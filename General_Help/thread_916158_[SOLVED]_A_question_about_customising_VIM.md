---
title: "[SOLVED] A question about customising VIM"
date: 2008-09-10
forum: General Help
---

### Post by Xnyper on 2008-09-10
Hello everyone,

I've been using Vim to write code for some of my programming classes and I really like the way it works.  I've picked up some habits doing this, and because of them I can edit code at lightning speed.  When I don't have homework I often write fiction.  I would like to carry over my uber-efficient code manipulation skills into the world of prose.

My problem is, while navigation within several lines of code works flawlessly; the same style of navigation within several paragraphs is quite cumbersome.  instead of 'j' taking me downwards a line, it takes me downwards a paragraph.  I suppose I could get around this with a '0' to take me to the top of the paragraph and then a '/' to skip to a word, but I would really like to set up two vimrc files, one that treated a line as a string of text terminated by a carriage return (for writing code), and one that treated a line as a horizontal row of text on the screen (for writing prose).

does anybody know what I would need to do to set such a thing up?  I have done a lot of searching, and found a lot of modifications of this sort, but nothing that fits my needs.

Thanks!

---

### Post by Stefanie on 2008-09-25
I always use "gj" and "gk" to go one "text" line down/up. you can also remap those to other keys or key combinations. 

if you want two different vimrc files you can remap "gj" and "gk" to "j" and "k" in the second one, i think it's as simple as that.

---

### Post by bingoUV on 2008-09-25
To do what Stefanie suggested automatically on the basis of file extension, do this:

1. Create a file .vim/ftdetect/text.vim

2. Enter the following in it:
```

au BufRead,BufNewFile *.txt             nnoremap k gk
au BufRead,BufNewFile *.txt             nnoremap gk k
au BufRead,BufNewFile *.txt             nnoremap j gj
au BufRead,BufNewFile *.txt             nnoremap gj j

```

3. This is assuming you use .txt extension for you fiction writing. Change the .txt in the above command to whatever is your favourite extension for fiction writing.

Now, j and k will do what you want automatically

---

### Post by Xnyper on 2008-10-02
I just knew there was a simple solution to my problem.  vim seems to be full of those.

I just knew someone helpful knew the solution to my problem. ubuntuforums seems to be full of those.

Thanks guys, that was exactly what I needed.

---

