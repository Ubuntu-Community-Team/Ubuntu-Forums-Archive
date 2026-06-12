---
title: "awk gensub problem"
date: 2008-08-10
forum: General Help
---

### Post by daveoily on 2008-08-10
well, I THINK gensub is the problem...

I have a script that I've been merrily using for a little while now thanks to the guys over on linuxquestions.org I'd never have thought of this solution to this problem otherwise, but I think my problem now is probably ubuntu specific...

[read the original discussion over on linuxquestions]("http://www.linuxquestions.org/questions/linux-newbie-8/bash-scripting-for-html-generation-490611/")

in brief, I have this script...
```
BEGIN{

print "<html>"

  print "<body>"

  print "<link rel=\"stylesheet\" type=\"text/css\" href=\"../1.css\">"

  print "<center>"

  print "<ul>"

}

{

  print "<li><a href=\""gensub(/\.mp3/ , ".html" , g )"\" target=\"rhs\">"$0"</a>"

  # and the other files ... 

  target = gensub(/\.mp3/ , ".html" , g )

  print "<html>" > target

  print "<body>" > target

  print "<link rel=\"stylesheet\" type=\"text/css\" href=\"../2.css\">" > target

  print "<center>" > target

  print "<a href=\"../music/"$0"\">"$0"</a>" > target

  print "</br>" > target

  print "</br>" > target

  print "<embed src=\""$0"\" autostart=\"true\">" > target

  print "</ul>" > target

  print "</center>" > target

  print "</body>" > target

  print "</html>" > target

  close( target )

}

END{

  print "</ul>"

  print "</center>"

  print "</body>"

  print "</html>"

}
```

it takes the filenames from a list and produces the html so that I can access my songs available for streaming from anywhere with a web connection and a half way decent browser :)

or rather, it DID do that (with a few minor quirks which aren't too much of a concern, if you're really good at this stuff then perhaps you could look at the thread listed above and maybe help me with that!)

now what I get when I try and run it is this....
```
c$ awk -f 1.awk list > index.html
awk: 1.awk: line 33: function gensub never defined
awk: 1.awk: line 33: function gensub never defined
```

I did a bit of round reading found that gensub is a function regularly called within awk (or is gawk more accurate?) so how come this error is being thrown at me?

have I not installed the right packages?

if I'm missing one, I'm clueless as to what it is that I need to fix it, I had a look in the repositories, but I don't fancy downloading everything that refers to awk for fear of conflicts between various implementations of awk and digging myself a deeper hole...

does anyone know what I've done wrong?

thanks in advance

dave

---

### Post by Mister.Vash on 2008-08-11
Try:
sudo apt-get install gawk

and see if it works after that

---

### Post by daveoily on 2008-08-11
thanks Mister.Vash :)

solved my problem, and seems to have automagically made it work with my now rather long song list

you've saved me a lot of work!

can I buy you a pint?

---

