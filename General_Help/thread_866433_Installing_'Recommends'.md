---
title: "Installing 'Recommends'?"
date: 2008-07-21
forum: General Help
---

### Post by TheForkOfJustice on 2008-07-21
I'm creating my own desktop metapackage (like ubuntu-desktop in the repos) and I wish to know how to get the recommends to install along with the dependencies.

I'm using Gutsy.  I don't know if that will affect any codes you provide.

---

### Post by fragos on 2008-07-21
Open up Software Sources Preferences and click the Updates Tab. Check the recommended box. If you're creating your own repository you'll need add it with the Third-Party Software Tab.

---

### Post by bodhi.zazen on 2008-07-22
you can do it from the command line with aptitude

sudo aptitude -r <package>

---

### Post by TheForkOfJustice on 2008-07-22
> **bodhi.zazen said:**
> you can do it from the command line with aptitude

sudo aptitude -r <package>

Thanks. I was hoping for a command line option since I can't use Synaptic when using Reconstructor (CLI only since it works with the ISO).

It's funny because I didn't see the -r switch when I looked at the aptitude help file.

Will that aptitude code work even if the package is just copied to the /var/cache/apt/archives directory or does it have to be in a proper online repository?

---

### Post by bodhi.zazen on 2008-07-22
-r is listed in the documentation :

[http://xgen.iit.edu/cgi-bin/man/man2html?aptitude+8](http://xgen.iit.edu/cgi-bin/man/man2html?aptitude+8)

If it does not work, you may need to :

```
--with-recommends
```

you can also --with-suggests or configure apt in /etc/apt/apt.conf

```
Aptitude::Recommends-Important
Aptitude::Suggests-Important
```

Not sure 'bout copying the .deb to /var/cache/apt/archives

---

### Post by TheForkOfJustice on 2008-07-24
> **bodhi.zazen said:**
> -r is listed in the documentation :

[http://xgen.iit.edu/cgi-bin/man/man2html?aptitude+8](http://xgen.iit.edu/cgi-bin/man/man2html?aptitude+8)

If it does not work, you may need to :

```
--with-recommends
```

I couldn't find -r initially but after a second look it did find the --with(out)--recommends version.

> you can also --with-suggests or configure apt in /etc/apt/apt.conf

```
Aptitude::Recommends-Important
Aptitude::Suggests-Important
```

I take it I'd have to make the /etc/apt/apt.conf file myself since one isn't there by default.  Just as well since I don't need to go that far. I just need the suggests from the one DEB file.

> Not sure 'bout copying the .deb to /var/cache/apt/archives

Unless someone wants to test it for me with a deb that isn't in the repos then I'll just have to wait for my version to be complete.

Thanks for your help :)

---

