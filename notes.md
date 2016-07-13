
## 1.Capitalization and punctuation
import re
def removePunctuation(text):
    """Removes punctuation, changes to lower case, and strips leading and trailing spaces.

    Note:
        Only spaces, letters, and numbers should be retained.  Other characters should should be
        eliminated (e.g. it's becomes its).  Leading and trailing spaces should be removed after
        punctuation is removed.

    Args:
        text (str): A string.

    Returns:
        str: The cleaned up string.
    """
    return re.sub(r'[^\w\s]','',text).lower().strip()
print removePunctuation('Hi, you!')
print removePunctuation(' No under_score!')
print removePunctuation(' *      Remove punctuation then spaces  * ')


## 2.Count the words

We now have an RDD that is only words.  Next, let's apply the `wordCount()` function to produce a list of word counts. We can view the top 15 words by using the `takeOrdered()` action; however, since the elements of the RDD are pairs, we need a custom sort function that sorts using the value part of the pair.

You'll notice that many of the words are common English words. These are called stopwords. In a later lab, we will see how to eliminate them from the results.
Use the `wordCount()` function and `takeOrdered()` to obtain the fifteen most common words and their counts.

TODO: Replace <FILL IN> with appropriate code

top15WordsAndCounts = wordCount(shakeWordsRDD).takeOrdered(15, key=lambda x: -x[1])
print '\n'.join(map(lambda (w, c): '{0}: {1}'.format(w, c), top15WordsAndCounts))
