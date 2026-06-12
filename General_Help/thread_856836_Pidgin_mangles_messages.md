---
title: "Pidgin mangles messages?"
date: 2008-07-11
forum: General Help
---

### Post by Skolem45 on 2008-07-11
Hi all, 

I'm running Hardy, have Pidgin installed (v. 2.4.1), and I use it over XMPP. I noticed that when I get messages with more than one line, all the lines but the first get mangled: the first few words seem to be skipped.

For example, when somebody sends me:

first line
foo_bar: baz
foo: bar baz
foo/bar: baz
foo: bar_baz
foo:bar baz
foo bar baz
baz: bar foo
(just in case it doesn't like foo)

what I get is:

first line
baz
baz
baz
bar_baz
baz
baz
foo
doesn't like foo)

The first line is always fine.

This didn't used to happen on the old Gaim... I frequently paste things like stack traces and pieces of logs into my chat window, so this behavior is a real show stopper for me. 

Any thoughts?
Thanks,
Gleb

P.S. My correspondent has Pidgin 2.4.3, also on Hardy. The manglage happens both ways.

---

