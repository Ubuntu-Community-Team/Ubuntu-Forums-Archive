---
title: "MySQL version upgrades"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by donco on 2009-10-30
:popcorn:

[rant]

Why? why?? why??? does Debian-sphere consider MySQL major.minor revisions to be upgradable? They aren't. They just aren't. apt (however you use it) should consider major.minor versions to be **conflicts** at best.

Notable examples are the 4.0 -> 4.1 (or greater) UTF8 corruption, but the APIs between releases are **never** compatable.

Ideally the Debian-sphere would allow MySQL releases to install in such a way that they could run alongside each other.  That would be invaluable when porting software & data over to the new release.  Supporting the old version wouldn't even be necessary, simply have the last good previous Debian/Ubuntu version packaged for the latest Debian/Ubuntu release for this purpose.

The libs and java packages are handled so well, with API changes handled as a completely separate package (with no upgrade path).  I simply wish MySQL was squared away like that.

[/rant]

:)

Regards,
-the donco

---

### Post by donco on 2009-10-30
To be absolutely clear.  By "release", and "major.minor", I mean any official MySQL release packaged/debianized should be an independent package.  The only MySQL "upgrades" within apt, would be security/bug fixes conducted by Debian/Ubuntu (which, admittedly, should be rather rare).

[rant]

There are simply too many examples of the SQL syntax changing between, say, MySQL release version 5.0.16 and 5.0.17.  Sure, this may make MySQL's SQL implementation more "correct".  Sure, it may be some SQL syntax that is so esoteric, 99% of applications won't notice.  Sure, we (as sysadmins) could pin the release in apt (whoops, should have added that to the poll options).

However, MySQL is the only package in all of our production environments, where this is ever an issue *due to API implementation changes* -- there are, of course, always examples of pinning to avoid bugs.

[/rant]

---

