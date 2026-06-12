---
title: "LaTeX question - How do I create a new style?"
date: 2008-10-22
forum: General Help
---

### Post by shaggy999 on 2008-10-22
\documentclass{post}
\title{\LaTeX question - How do I create a new style?}
\begindocument{post}
I apologize if this is the wrong forum, but there didn't seem to be a right forum for this.

I am in the middle of writing a document in LaTeX and there are some things that I know I will want to mark up in a special way at some point, but I don't know how I will mark them up. Until then I'd like to be able to encapsulate the text with some kind of command that tells it to use a certain custom style. Then later when I'm finished with producing the content of the document I can go back and fiddle with the design.

Is there a way to do this? Basically I want to be able to do something like:

\style1{Some text goes in here.}

This way I can move on with the rest of the document knowing that it's ready to accept a style later on when I get around to it.

\enddocument{post}

---

### Post by hugmenot on 2008-10-23
```
\newcommand{\style1}[1]{#1}
```

then later change to, e.g.:

```
\newcommand{\style1}[1]{\emph{#1}}
```

if you want to redefine in the middle of the document you use 

```
\renewcommand{\style1}[1]{\textbf{#1}}
```

---

### Post by hugmenot on 2008-10-23
your post syntax is a bit weird.

---

### Post by shaggy999 on 2008-10-23
Oh, how simple! :) Thanks!

And I made my post with LaTeX commands just because I'm practicing and thought it would be fun. ;)

---

