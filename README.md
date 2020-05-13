# vomBuchInAnki
Creates German vocabulary Anki cards from notes made in Google Play Books. Great for advanced German learners.

<img src="/example.png" alt="Example" width="70%" height="70%">

## Installation
You need to have [Anki](https://apps.ankiweb.net/#download) installed: `sudo apt install anki` plus the add-on [AnkiConnect](https://ankiweb.net/shared/info/2055492159) (and your account connected of course).
 
 1. Clone this repo.
 1. `bash installpreqs.sh` to install the prerequisites ([SFST](https://www.cis.uni-muenchen.de/~schmid/tools/SFST/) and [Beautiful Soup](https://www.crummy.com/software/BeautifulSoup/)).
 1. Set your profile in the profiles folder.
 
 ## Usage
 1. Markings provided should either be a single word, an idiom or a phrase beginning and ending with the parts of a separable verb (e.g. _ging oft damit ein_).
 1. `python main.py`
 1. Specify a profile if several exist.

## What it does
1. Markings are cleaned with phrases are treated as trennbare Verben or idioms, and then [Zmorge](https://pub.cl.uzh.ch/users/sennrich/zmorge/) is used for lemmatization and part-of-speech determination.
1. Every lemma + POS pair found (one marking can lead to several pairs) is queried to [PONS](https://en.pons.com/p/online-dictionary/developers/api) using the API you provided in the profile and according to their terms.
1. The best translation to be used as a card is picked from the entry, alongside with an example, to create an Anki note.
1. Notes are created using AnkiConnect.
1. Markings for which no translation/lemma was found (~5%) are written in the path specified in the profile.