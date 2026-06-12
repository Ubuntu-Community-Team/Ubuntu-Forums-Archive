---
title: "[SOLVED] Installing a package from my Home folder"
date: 2008-09-05
forum: General Help
---

### Post by Dyffo on 2008-09-05
I have downloaded a programme from a source package .tar, this I have opened with Archive Manager and the whole file is now in my Home Folder. I cannot figure out how to install this package.I know that somehow I have to get this into the Terminal ! Help please.:confused:

---

### Post by fragos on 2008-09-05
Hopefully you've used Synaptic to install "build-esentials". Place the tar in it's own folder. Right click the tar icon and select "Extract here". If the result is another folder, open it. You want to find a file called "configure". Open a terminal window and "cd {folder with configure}. Now there are 3 command line steps.

./configure
make
sudo make install

Each step may take some time to run and if there are dependancy problems you will be informed.

---

### Post by zvacet on 2008-09-05
Right click on tar file and select **unpack here**.That will create folder.Look inside if is there **Read me** or **Install** file.In most cases it works like this:

from terminal go to the unpacket folder and then run 

1.configure
2.make
3. sudo make install
[B]
Be sure that you have build-essential installed before you do this.[/B]

---

### Post by panayk on 2008-09-05
Or you can install the package checkinstall from synaptic, and replace the third step with:

3. sudo checkinstall

It will now ask you to fill in some information about the package (optional really) and then it will put your built sources in a .deb package, and install it.
That way you can remove or reinstall your program just like you'd gotten it in .deb form.

---

