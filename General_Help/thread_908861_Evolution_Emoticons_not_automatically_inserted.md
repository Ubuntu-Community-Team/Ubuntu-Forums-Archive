---
title: "Evolution Emoticons not automatically inserted"
date: 2008-09-02
forum: General Help
---

### Post by newagelink on 2008-09-02
[COLOR="Indigo"]This is an old problem, but every old thread has been archived.[/COLOR] (E.g. [a previous thread]("http://ubuntuforums.org/showthread.php?t=479373"), [another thread]("http://ubuntuforums.org/showthread.php?t=428555").) [COLOR="Indigo"]I'm creating this thread because there appear to be no current threads about it and I'm hoping for a discourse to help me fix it ... I'm using Ubuntu 7.10.

Someone posted [a link to a bug report]("https://bugs.launchpad.net/ubuntu/+source/gtkhtml3.14/+bug/91149"), for which a patch was posted and the problem presumed fixed, although users apparently continued having issues. [The following comment]("https://bugs.launchpad.net/ubuntu/+source/gtkhtml3.14/+bug/91149/comments/15") concerns me:[/COLOR] > gtkhtml3.14 (3.15.91-0ubuntu1) gutsy; urgency=low

  * New upstream version:
    Bug Fixes:
    - #262907: Incorrect cursor navigation & deletion for composite
      glyphs in indic languages
    - #270487: autourlified URLs not html-escaped
    - #343994: User can not delete more than 1 line/column in message composer
    - #346004: It is impossible to insert plain rule with length
      specified in pixels
    - #419350:> Solves the problem of incorrect/inappropriate emoticons display
      (LP: #91149)

 -- Sebastien Bacher <email address hidden> Mon, 27 Aug 2007 18:23:22 +0200

[COLOR="Indigo"]I open Synaptic Package Manager to find that I have Package "gtkhtml3.14" already installed: Installed Version and Lastest Version being "3.16.1-0ubuntu1". (Shouldn't that be the end of it?) Below it I see Package "gtkhtml3.8", not installed. gtkhtml3.14 has the ubuntu logo to the left of its Package name; "gtkhtml3.8" does not. I presume that means Ubuntu supports the former package (i.e. the one installed) and not this 3.8 one, a remnant of a previous edition ...?

Any ideas what my problem is? Any help would be greatly appreciated. It looked from one thread as if a few installed that 3.8 package and manually created links for Evolution to follow to the emoticon files, fixing it as a workaround. (It sounds complicated and less than ideal, as if I'd be hacking the software more than actually fixing it, and using an obsolete package to do so ... not to mention that I have no idea where to begin.)[/COLOR]

---

