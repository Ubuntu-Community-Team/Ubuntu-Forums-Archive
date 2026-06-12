---
title: "problems installing xerox document centre 230 ps"
date: 2009-03-18
forum: Hardware
---

### Post by anton12345678 on 2009-03-18
hallo,

i am trying desperately to install a xerox document centre 230 ps network printer on my ubuntu 8.10.

using:

 lpd://[IP]/515 

as device-uri in the ubuntu printer installation, i can send print jobs to the printers queue, so i believe this works so far.

nevertheless the printer refuses to print. and has to be restarted to work with other computers again. so i suppose it's a driver problem.

ubuntu doesn't offer an automatic installation, so i downloaded the windows driver package from the xerox site and used the ppd file (xxd2303b.ppd) provided there. hence it can talk with the printer but i cannot print.

i also tried other drivers (e.g. HP LaserJet 4/4M 600DPI Postscript) supposing that any postscript driver should work, but i'm obviously wrong.

a direct installation via localhost:631 doesn't change anything.

now i'm out of ideas or anything to be found in the internet.

does anybody have an idea?

thanks
anton

---

### Post by halitech on 2009-04-09
I'm assuming you mean the DC 230ST. There is no Linux driver (or Unix for that matter) for that machine and the windows ppd files aren't going to work either. 

I hate to say it but I think you have a paper weight in this one as far as using it in linux goes.

---

