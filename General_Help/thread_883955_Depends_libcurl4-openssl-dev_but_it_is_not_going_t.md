---
title: "Depends: libcurl4-openssl-dev but it is not going to be installed"
date: 2008-08-08
forum: General Help
---

### Post by S3loth on 2008-08-08
I get this error while trying to install Boxee. When I try to install the libcurl4-openssl-dev, it does the same thing only with a different file.
P.S.
I have some invites to Boxee if anyone's interested.

---

### Post by Taxman415a on 2008-08-08
Can you tell us what version of Ubuntu you are running and give us the output of ```
aptitude why-not libcurl4-openssl-dev
```
And from whatever directory you have this Boxee deb in, run ```
dpkg -I boxee-whatever-the-rest-of-the-filename-is.deb
```

---

### Post by S3loth on 2008-08-09
I'm running Hardy, and this is the output.

```
i   nvidia-glx-new      Suggests  nvidia-new-kernel-source (>= 169.12)          
p   nvidia-new-kernel-s Recommend devscripts                                    
ource                   s                                                       
p   devscripts          Suggests  cvs | subversion | svk | tla | bzr | git-core 
                                  | mercurial                                   
p   bzr                 Suggests  python-pycurl                                 
p   python-pycurl       Suggests  libcurl4-gnutls-dev                           
p   libcurl4-gnutls-dev Conflicts libcurl-dev                                   
p   libcurl4-openssl-de Provides  libcurl-dev                                   
v 
```

I'm not using a deb, but Synaptic, from the repo [http://apt.boxee.tv](http://apt.boxee.tv)

---

### Post by S3loth on 2008-08-10
Okay, I fould the problem. I guess it was the mirror I was using for my repos. I just did a "Check for Best Server" and now it works.

---

