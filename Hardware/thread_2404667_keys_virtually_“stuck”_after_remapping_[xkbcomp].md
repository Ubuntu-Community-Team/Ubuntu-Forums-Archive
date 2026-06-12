---
title: "keys virtually “stuck” after remapping [xkbcomp]"
date: 2018-10-26
forum: Hardware
---

### Post by Bifidus on 2018-10-26
[COLOR=#242729][FONT=Arial]Hello

**My configuration:**[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I use a keyboard, a mice (currently Roccat Nyth), and a Tartarus Chroma v2 (a sort of mini keyboard for just one hand). And other input peripherals non related to my problem.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]When i play World of Warcraft, it's with Tartarus+mice. I barely touch the keyboard. The Tartarus, by default, is mapped as a regular keyboard, which is unsuitable for my needs.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]It don't have any usable driver for linux (openrazer have open issues for the Tartarus since years, so i don't expect it to work soon, if ever).[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]But it can be remapped with xkbcomp, as i learned on this page: [https://lampjs.wordpress.com/2015/06/26/remapchange-your-secondaryusb-keyboard-keys/](https://lampjs.wordpress.com/2015/06/26/remapchange-your-secondaryusb-keyboard-keys/)[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]There is my dump (without remapping) xkb file: [https://pastebin.com/XpR9RDPd](https://pastebin.com/XpR9RDPd)[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]There is my remapped file: [https://pastebin.com/3pXSKiWX](https://pastebin.com/3pXSKiWX)[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]It seem to work: checking with xev, i can confirm i have the remapped keys i want on the Tartarus, while the regular keyboard keys are unchanged.

[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]**The problem:**[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]When i use any key of the Tartarus with any modifier (shift, ctrl, alt), it switch back to it's unmapped state, and became "stuck" in that state until i press the physical key who is bind to that unmapped state (usually on my regular keyboard, but it also work with the Tartarus), to "unstuck" it (and it also make it switch back to it's mapped state).[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]If i unmap the Tartarus, i can't reproduce the problem, so i highly suspect my configuration file to be bad. But i have no idea what's wrong in it... I read the Arch Wiki page about xkbcomp, but barely understood it.

Help! ^^[/FONT][/COLOR]

---

