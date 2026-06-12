---
title: "Language support"
date: 2008-08-22
forum: General Help
---

### Post by Ponhovo on 2008-08-22
I'm in ubuntu 7.10 with gnome

I wanted to change the language of my ubuntu to spanish
so I went to ubuntu menu, system, administration, Language Support, typed my password, ticked the spanish box and applied
well, it went everything ok, until it started to set the language-pack-es up

it hangs in here:
Generating locales...
es_AR.UTF-8...

and stands in there forever

so I searched over the internet for help
the solution was to kill the process
to some users worked, but didn't to me
and I wouldn't ever accept it as a final solution
I'd like to know what the hell is going on

well, it didn't appeared in the list of languages in the Language Support [at adiministration]
1st - is it the wrong place to set the language?

so I removed the english language-pack to see if would work
it didn't change at all, even after rebooting
so I tried to install it back, but it hangs forever in the same prompt

so, when things go bad, I kill the process and run 'sudo dpkg --configure -a' but it always hangs in the same prompt
2nd - do someone know how to let the installation go on?

---

