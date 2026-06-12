---
title: "[SOLVED] How to install Openoffice Math?"
date: 2008-10-12
forum: General Help
---

### Post by SukruH on 2008-10-12
Hello. I need Openoffice Math to add equations to my documents, but I don't know how to install it. Any help?

---

### Post by Idefix82 on 2008-10-12
This is not really answering your question but the most efficient and pretty way of typesetting documents with equations is to use latex. For this you need the texlive package and just a simple text editor like gedit.

If you want to know more, just google for latex. You will find lots of resources. If you then need help to get started, just reported back here.

Sorry not to answer your question, I have never worked with any WYSIWYG editors for maths formulae.

P.S.: Just had a look, the package you need is in the repositories. Just type in the terminal
```
sudo apt-get install openoffice.org-math
```
or open the Synaptic Package manager under System->Administration and search for "openoffice math". Then left click the square next to the package openoffice.org-math and click "mark for installation". Now just click "Apply".

---

