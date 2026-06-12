---
title: "Installing non packaged software"
date: 2009-07-05
forum: Installation &amp; Upgrades
---

### Post by spip on 2009-07-05
As part of wanting an up to date and custom version of ffmpeg, I followed the instructions from the following forum thread on how to install ffmpeg manually:

[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

While this has worked, installing the generated debian packaged required me to uninstall some packages because there were some of the files the generated ffmpeg package was trying to install were already part of installed packages.

One example is libavcodec52.

I still have the library installed, however from a package management point of view I do not have the libavcodec52 package installed.  So now, as I try to install kdenlive, synaptic determines that the libavcodec52 package needs to be installed.  I know about "holding" packages with apt, but I don't know if this will help as the libavcodec52 package isn't installed, I just have the library from installing another package.

What is the best way to proceed from there?

- Let libavcodec52 be installed as a debian package resulting from the kdenlive dependency and be done with it?

- Remove my local libavcodec52 files and then let the package be installed?

- Do not install the libavcodec52 package even if it is a dependency knowing that I have the necessary files already installed? (however every future package that I install in the future which will have a libavcodec52 dependency will ask me to install it)

- Other possibilities I am not thinking of right now?

I am sure this is a typical problem in package management.  You end up manually installing some things that are represented in packages in as granular a way they would have been with the stock ubuntu install.  I'm just curious what people do about this in general, as it is often necessary to manually fetch/build/install software.

Thanks!

---

