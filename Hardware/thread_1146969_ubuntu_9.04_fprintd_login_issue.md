---
title: "ubuntu 9.04 fprintd login issue"
date: 2009-05-03
forum: Hardware
---

### Post by wangcgfan on 2009-05-03
dell xps m1530,ubuntu 9.04
install fprintd for fingerprint reader
 vi /etc/pam.d/common-auth

add line

"auth sufficient pam_fprint.so"

to the very end 

login screen, i can use fingerprint reader to login,but i should enter both the password and swap my finger to login .
 how can i login either with password nor swaping my finger.

in my opensuse 11.1 ,i can login with password or fingerprint reader.
i do not like login with both password and fingerprint reader ,that is to boring.

does that have something to to with comm-auth file?

here is my common-auth file
> 
# To take advantage of this, it is recommended that you configure any
# local modules either before or after the default block, and use
# pam-auth-update to manage selection of other modules.  See
# pam-auth-update(8) for details.

# here are the per-package modules (the "Primary" block)
auth    [success=1 default=ignore]      pam_unix.so nullok_secure
# here's the fallback if no module succeeds
auth    requisite                       pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
auth    required                        pam_permit.so
# and here are more per-package modules (the "Additional" block)

# my own config lines
# auth required pam_fprint.so
 auth sufficient pam_fprint.so
#auth required pam_unix.so nullok_secure
# finished my own config lines

# end of pam-auth-update config



---

### Post by wangcgfan on 2009-05-04
any one know how to deal with this??

---

### Post by madmax.santana on 2009-10-11
That's the problem! nobody seems to know. And the ones who know rarely come to visit forums.
I had a problem with sound in my laptop. I searched and surfed and sweat all over the internet for this problem. A thousand opinions about he problem.

Then in the end I came accross a blog entry which was something about linux development... Here, in Linux development, an exact and accurate solution of the problem was written in plain simple words...

End-result was happy. I found the solution... But only if that Linux geek had been live on forum and helping, he could have read my post in the forum and I did not have to sweat all over it...

There is a brighter side to this, anyway! While I was searching, I came accross many situations which enhanced and boosted my experience with Linux...
Howsoever, more help whould be available on the forums directly, anyway.

---

### Post by jlrodasr on 2009-10-14
Some information can be found here [http://aldeby.org/blog/index.php/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops#fingerprint](http://aldeby.org/blog/index.php/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops#fingerprint)

Looks like you have to place *auth sufficient pam_fprint.so* at the top of the file, not at the bottom.

---

### Post by Naaktgeboren on 2011-04-23
Ubuntu packages with fprintd are now available at:

[https://launchpad.net/~fingerprint/+archive/fprint]("https://launchpad.net/~fingerprint/+archive/fprint")

---

