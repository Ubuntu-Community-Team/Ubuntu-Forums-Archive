---
title: "Vim Highlighting"
date: 2008-10-23
forum: General Help
---

### Post by Printscreen on 2008-10-23
So ive been messing around in the full version of Vim. I was on this wiki here learning about the different commands to get number lines.

[http://vim.wikia.com/wiki/Display_line_numbers](http://vim.wikia.com/wiki/Display_line_numbers)

So i dont really remember what i typed exactly, but now vim highlights everything in yellow, and its quite annoying to code with a black background and every line highlighted in yellow.

i think the exact command i typed in was

:highlight LineNr term=bold cterm=NONE ctermfg=Black ctermbg=NONE gui=NONE guifg=Black guibg=NONE

I think its defaulting to a yellow highlight since i was stupid enough to put both as black. Ive tried different combos since then, and it only affects the number lines, and not the main body of text. Im ssh'd into my dev environment.

So, i think ive checked my local vrc file and it looks fine. Since im new to Linux, is there a vrc file on the server im logging into dictating the look of my vim, or is it pulling it from my local machine? If i vim something on my local machine its fine, its only when editing files in my dev environment. More importantly, does anyone have any idea how to just get it to restore to the default?
Thanks

---

### Post by SoCalChris on 2008-10-23
Look for the .vimrc file in your home directory of the remote machine. You should be able to edit, or completely delete it to revert it back to the default.

---

