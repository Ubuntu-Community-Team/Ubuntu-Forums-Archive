---
title: "[SOLVED] Is there any simple way of adding # as command in vi for multiple lines?"
date: 2008-08-21
forum: General Help
---

### Post by abcuser on 2008-08-21
Hi,
in Ubuntu 8.04 using vim editor to edit bash scrip files I regularly add/remove # character at the beginning of line to make/remove comments.

Is there any simple way to add for example # for 10 lines?
Thanks,
Abcuser

---

### Post by ghostdog74 on 2008-08-21
Say you want to change line 3 to line 7
1) go to line 3, press ma
2) go to line 7, press mb
3) go to esc mode, type in 
```

a',b's/^/#

```
Always go to the VIM manual if you are stuck.

---

### Post by SeanHodges on 2008-08-21
A quick solution would be to use macro's. You can record your actions on a line, then ensure you record moving down a line at the end. You can then move the cursor to the top of the code you want to comment and tell Vim to play back the macro for a number of lines. This will create the macro you want: 

<Esc>qa
0i#<Esc>j
q

You can then use it by moving to the top of the code you want to comment and type this to comment 10 lines:

10@a

The disadvantage is that you will need to record the macro each time you restart Vim. To avoid this (as a more permanent solution), you will need to create a function in your .vimrc file. An example of such a function can be found here:

[http://www.vim.org/tips/tip.php?tip_id=369](http://www.vim.org/tips/tip.php?tip_id=369)

This particular example isn't great, I'm sure there are better ones out there. To make this one work for you you'd need to change references of "//" to "#" and perhaps create a key mapping.

Be sure to post back if you go down this route and hit any specific problems. I'd recommend searching the Vim wiki for commenting functions before writing your own.

---

### Post by abcuser on 2008-08-22
SeanHodges,
thanks for suggestion. I did the following:
1. I downloaded vim script from [http://www.vim.org/scripts/script.php?script_id=1208](http://www.vim.org/scripts/script.php?script_id=1208)
2. I saved it in my home directory as .vimCU.vim  (I added first dot at filename to make it hiden when ls command is executed at terminal)
3. I added new line in my home directory file .vimrc:
```
source ~/.vimCU.vim
```
4. Closed all vim windows if opened.
5. Start vim editor and "commenting" is up and running.

How it works:
1. If in text mode press <Esc> to enter in command mode.
2. Press v to enter into visual mode.
3. Press left or right keys to mark text (lines).
4. Press ,# to make commented all lines that were market in step 3.
or press ,3 to uncommenten lines

Notice 3 and # are on the same keyboard key.

This trick will save me a lot of time.

Thank you very much for suggestion,
Abcuser

---

### Post by abcuser on 2009-01-06
Hi,
just two more tips for marking out the text I have found out.

I. Instead of using v (step 2) to enter visual mode for by characters, you can also use V to entering into visual mode by line to mark whole lines instead of just marking characters.

II. Instead of using keyboard to mark text (steps 1 to 3), you can also use mouse if executing command:
```

:set mouse=a

```
If you would like to make mouse permanent you can write this command in user's home directory file .vimrc
Regards

---

