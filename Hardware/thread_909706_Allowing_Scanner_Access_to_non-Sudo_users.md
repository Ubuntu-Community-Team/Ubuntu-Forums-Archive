---
title: "Allowing Scanner Access to non-Sudo users"
date: 2008-09-03
forum: Hardware
---

### Post by Stoffer on 2008-09-03
I'm running kubuntu, but I don't think it'll make a difference here.  I used the following instructions to get scanning to work on my Canon Pixma MX300 All-in-One: [http://mp610.blogspot.com/2008/04/give-your-scanner-new-freshly-sane.html](http://mp610.blogspot.com/2008/04/give-your-scanner-new-freshly-sane.html)

Everything pretty much worked out, except for one thing.  There's a section in the instructions that tell you to replace the original libsane.rules file with the one proviced in the sane CVS, in order to allow non-sudo users to access the scanner.  The problem is, I never had an original libsane.rules file, so placing the new one in that directory did nothing.

Now the only way I can access my scanner is if I sudo into whichever program I'm using (kooka, gscan2pdf).  It works, but it's a huge pain.  It seems as though there should be a simple solution for this.

Thanks!

---

