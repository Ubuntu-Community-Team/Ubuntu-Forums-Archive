---
title: "How to install Rubber for Gedit LaTeX plugin?"
date: 2009-06-30
forum: Installation &amp; Upgrades
---

### Post by pooja on 2009-06-30
Hi everybody,
I want to use Gedit to compile LaTeX documents so I downloaded the TeXLive packages. Then I enabled the LaTeX plugin in Gedit but when I go from Tools > LaTeX --> PDF nothing comes up, and there's an error message in the Bottom panel that runs like this: 
```
rubber -- inplace --maxerr-1--shorrt--force--warn all "$filename" 
```
and a series of other errors related to it.

I went to Gedit's website and found I have to install a bug fixer called "rubber". I extracted the folder "rubber-1.1" to ~/Desktop but I don't know how to install it among the plugins of Gedit. 
Can someone please tell me step-by-step what to do next? 
I understand I have to use the Terminal but what should I write on it? 
Please help me, I installed ubuntu on my PC just 3 days ago.

---

### Post by hugmenot on 2009-07-02
Rubber is a command-line tool that is used by the Gedit Latex plugin. It is a Latex build system dealing with compilation runs and extracting the syntax and other errors.

To install simply delete the archive and the folder you extracted and then install it with Synaptic or through the terminal:

```
sudo apt-get install rubber
```

---

