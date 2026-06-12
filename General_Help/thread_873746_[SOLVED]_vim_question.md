---
title: "[SOLVED] vim question"
date: 2008-07-29
forum: General Help
---

### Post by PGScooter on 2008-07-29
Hi, how can I move up and down by visual lines (that is, not line breaks, but by the lines as they appear on the screen)?

If my question does not make sense, let me know.

thanks

---

### Post by derrick81787 on 2008-07-29
> **PGScooter said:**
> Hi, how can I move up and down by visual lines (that is, not line breaks, but by the lines as they appear on the screen)?

If my question does not make sense, let me know.

thanks

I've wondered that, too, and I don't really know.  I know you can run the command ':set nowrap' so that the lines are not wrapped and then the visual lines are the actual lines, but that may not be exactly what you're looking for.  You can also put that in your ~/.vimrc if you would like that to be the default.

As far as keeping word-wrap on and doing what you asked, I'm not really sure.  Sorry I couldn't be more help, but if it's possible, someone else will probably know.  Somewhere there are some really good forums that I've visited in the past, but after some googling around, I can't seem to find them...

- Derrick

---

### Post by PGScooter on 2008-07-29
hey Derrick..

I might search around in a week or two when I have more time. I have yet to find a good vim forum. The thing with this is, you can't really create a macro or map some commands.

Well, I'll let you know if I make any progress. I'm convinced that there's a solution out there somewhere.

scott

---

### Post by PGScooter on 2008-07-30
Ok I found it.

You just have to preface the normal moves with a g.
That is, to move visually up one line, do ```
gk
```

It's time to do some mapping :)

---

### Post by derrick81787 on 2008-07-30
> **PGScooter said:**
> Ok I found it.

You just have to preface the normal moves with a g.
That is, to move visually up one line, do ```
gk
```

It's time to do some mapping :)

Awesome! I'll remember that.  Thanks for the solution.

- Derrick

---

### Post by PGScooter on 2008-07-30
I just mapped the up and down arrows to it, and if you leave the left and right arrows the same, it works well. However, it is a little awkward having to move to the arrow keys and then back I guess.

---

