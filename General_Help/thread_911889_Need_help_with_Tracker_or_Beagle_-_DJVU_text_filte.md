---
title: "Need help with Tracker or Beagle - DJVU text filter"
date: 2008-09-06
forum: General Help
---

### Post by pelikan555 on 2008-09-06
On the tracker-list mailing list I found out how to make Tracker search the text 'layer' of DJVU files. Here is the link: [http://www.mail-archive.com/tracker-list@gnome.org/msg01799.html](http://www.mail-archive.com/tracker-list@gnome.org/msg01799.html)

I would love to add this functionality to Tracker (like Apple's Spotlight seems to do), but there is no reference in the above link where to put the script or what to do with it. 

Does anyone know where it should go?

I found more exact instructions on how to make Beagle work with DJVU, but despite having installed all Beagle packages I cannot find the external-filters.xml file to add the filter to ([http://beagle-project.org/ExternalFiltersRepository](http://beagle-project.org/ExternalFiltersRepository)).

Help on either of these points would be very handy indeed!
Thanks.

---

### Post by pelikan555 on 2008-09-13
**bump**

Thanks

---

### Post by tschew on 2008-11-15
Disregard my previous post. I think I had put djvu_filter there some time ago and then forgot about it. Further, I think the script is wrong as it does not produce any output when used on a djvu file.

The following, however, should work:

#!/bin/sh
nice -n19 djvutxt "$1" "$2"

This produces plain text output from a djvu file. All that's needed now is some way to make tracker aware of the djvu_filter. However, I have no idea how to do that. My guess is that an "extract-module" must be written. (see /usr/lib/tracker/extract-modules )

---

