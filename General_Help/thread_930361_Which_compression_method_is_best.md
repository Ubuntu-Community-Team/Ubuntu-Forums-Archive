---
title: "Which compression method is best?"
date: 2008-09-25
forum: General Help
---

### Post by newbuntuxx on 2008-09-25
Hey 

When I right click any folder on my desktop, and select: create archive, i get a window with many compression options, namely:

tar.gz
tar.bz2
tar
zip
rar
ar
ear
jar
war

Is there a specific task that a certain method is for? like say, .zip is best at compressing a folder of pictures, while tar.gz is best at compressing a folder of text? or are they all the same and as efficient? 

If there is a difference, could someone rank them based on efficiency and speed and perhaps shed some light on when to use them.

thanks

PS. I have read a few papers on the Huffman algorithm and the LZ77 method. I think the idea is brilliant, but the implementation thereof requires a high IQ. The answer that i am looking for in this thread is a simple one geared towards the average user. So, unless it is necessary, please omit the technical niceties. thanks again

---

### Post by lisati on 2008-09-25
I agree, some of the technical niceties of the various techniques are over my head too......
Of the compression types in your list that I recognize, I think I read somewhere that some of them are better than ZIP

---

### Post by estamand on 2008-09-26
I am by far no expert in file compression.  Myself I like 7zip as i've found that it offers the most compression in file size.

the Ubuntu Guru says:

[http://ubuntuguru.wordpress.com/2007/03/09/whats-the-best-file-compression-method/](http://ubuntuguru.wordpress.com/2007/03/09/whats-the-best-file-compression-method/)

---

### Post by newbuntuxx on 2008-09-26
thanks for the useful link estamand. 

Question: how come 7zip is not among one of the default compression options in ubuntu?

---

### Post by oldsoundguy on 2008-09-26
Personally I like .rar .. simply because I can use it in both Linux and Windows and use it to move a gang of video or music with little or no issues.  BUT that is my preference and my reason for using it.

When it comes to standard data, not a clue!

---

### Post by jerome1232 on 2008-09-26
Just a side note nearly all music and picture formats are already compressed (jpeg, mp3, ogg) and won't compress much under any compression algorithm, they can even bloat a bit.

text files will compress like there's no tomorrow though. (as in 2 GB text file down to 20 MB I think that particular file was a .rar archive)

---

### Post by vikramaditya on 2008-09-26
i like a garlic press, as the squeeziness whilst compressing a clove of garlic with it is oddly satisfying. :)

---

### Post by Nepherte on 2008-09-26
I believe .tar.bz2 gives a higher compression ratio, but it takes more time to extract. Most of them use the huffman coding algorithm for compression. Beware that if you compress for example .jpg pictures or .avi movies, it will barely do anything as .jpg and .avi are compressed formats.

---

### Post by Sycron on 2008-09-26
I like zip, tar.bz2 and rar. Since with Ubuntu I use when I can only tar.bz2.

---

