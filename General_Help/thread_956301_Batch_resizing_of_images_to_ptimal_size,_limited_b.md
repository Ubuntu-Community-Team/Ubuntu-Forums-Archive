---
title: "Batch resizing of images to ptimal size, limited by a4 page format"
date: 2008-10-23
forum: General Help
---

### Post by kwaanens on 2008-10-23
Hi good people

I have a bunch of images that I'd like to batch resize, so that they are resized as large as possible, but staying within the constraints of an a4 page.

Does anyone have a nice imagemagick script to do this?

Thanks!

-- Ketil

---

### Post by geirha on 2008-10-23
I guess what you really want is to change the aspect ratio to 1:sqrt(2) as defined by [ISO 261](http://en.wikipedia.org/wiki/ISO_216)? If so, you'll either have to crop the image or scale it vertically or horizontally. Cropping would be the best choice in my opinion, but how will the script know which part to remove?

---

### Post by _sAm_ on 2008-10-23
Perhaps you could use Phatch: [http://photobatch.stani.be/](http://photobatch.stani.be/)

Its in the repos.

---

### Post by kwaanens on 2008-10-23
Looks interesting. I'll give it a try. Thanks!

-- Ketil

---

