---
title: "PPAP: Unique Protocol to Protect (?) Email Attachments in Japan"
date: 2022-09-09T06:00:00-04:00
draft: false

# post thumb
image: "images/post/email.jpg"

# meta description
description: "PPAP, an email attachment protection protocol (?) in Japan."

# taxonomies
categories:
  - "Cybersecurity"
tags:
  - "Protocol"
  - "Mistake"

# post type
type: "post"
---

<hr>

#### What's covered in this post?

* PPAP: A unique "protocol" to secure email attachments in Japan
* Is PPAP really secure?

<hr>

##### PPAP: A unique "protocol" to secure email attachments in Japan

Most people will probably agree that Japan cultivates a unique culture of its own. From ***kimono*** to ***anime*** and everything in between, Japan has a track record of differentiating itself from the rest of the globe. Sharing no borders with its neighboring countries, Japan's [Galápagos syndrome](https://medium.com/@alxgcs/understanding-the-galapagos-syndrome-through-japans-unique-quirks-967dcbc05d47) never fails to surprise us with the alternative paths human evolution can take.

So maybe it's not surprising to hear that Japan has popularized a particular protocol to secure email attachments. It's called PPAP, but don't confuse this with Pikotaro's [PPAP](https://www.youtube.com/watch?v=0E00Zuayv9Q) where he combines a pen, a pineapple, an apple, and another pen. It's not quite the same, but in fact, it might be a tad simpler than that.

The acronym PPAP explains the protocol for itself in Japanese. It stands for:

**P**assword付きZIPファイルを送ります ("Send the password-encrypted zip file")\
**P**asswordを送ります ("Send the password")\
**A**ngoka（"Encrypt")\
**P**rotocol 

Let's break this down a little. First, the sender compresses files to be sent into a password-protected zip file. The sender sends this encrypted zip file as an email attachment to the receiver. The sender then sends a separate email to the receiver with just the password in the email body. At this point, the receiver has received 2 emails: one with an encrypted zip file attachment and another with the password. The receiver uses the password to decrypt the zip file to uncompress the files of interest.

<hr>

##### Is PPAP really secure?

Files were transmitted securely, because the compression process used encryption... right? Well, not quite. In fact, this "protocol" has some major flaws so detrimental to the point where these files essentially have no security guarantee:

1. PPAP is prone to a man-in-the-middle attack. If an adversary can tap into the communications channel, it will retrieve both the encrypted zip file and the password to decrypt it. At that point, not only can the adversary decrypt and view the contents of the encrypted zip file, it can modify the contents without getting detected.

2. [Encrypted zip files](https://www.cyberscoop.com/zip-files-encryption-security-wyden-nist/) are actually terrible at maintaining confidentiality. This is because typical, encrypted zip files have no protection against failed decryption attempts. If an adversary fails to decrypt an encrypted zip file, it can just try it again. Since decryption happens offline, the adversary has unlimited number of attempts in an unrestricted amount of time to crack the zip file. With modern computers and cloud computing, this isn't a difficult task.\
Let's say you somehow modified the specification of encrypted zip files in such a way that after a certain number of failed decryption attempts, the zip file cannot be decrypted. This is very easy to circumvent, because the encrypted zip file can simply be copied, and a brute-force decryption attack can happen parallelly across the encrypted zip file copies. 

3. If the encrypted zip file contained malware, it will make it harder for both signature-based and behavior-based (e.g. sandbox detection) antivirus software to detect it. (This isn't necessarily a flaw specific to PPAP, but any transmitted data that are encrypted has this issue)

All in all, PPAP isn't really secure, if not secure at all. The practice of using PPAP has been quite popular in Japan, and it still is today. The false sense of security is a major issue which requires massive re-education of Japanese IT users. Instead of PPAP, let's stick to file sharing protocols like [SFTP](https://www.ssh.com/academy/ssh/sftp) for now. 

Shuta