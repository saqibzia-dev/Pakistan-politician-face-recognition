

# Pakistani Politician face Recognition
  
Demo: <a href="https://politicianrecognition.herokuapp.com/">Pakistani Politician face Recognition</a>



## Objective
The purpose of this project is to recognize faces of Pakistan's top politicians.This model is trained on Asif Ali zardari,Shahbaz Sharif,Sheikh Rasheed,Imran Khan Images and it use computer vision and machine learning to recognize their faces .This project is made to learn how to extract facial features and use them to recognize faces
using opencv and machine learning techniques.


### Approach Used:
* **Data Collection**: Data was collected from google images using fatkun extension.
* **Feature Detection** : <ul>
  <li>Face and Eyes are detected using open cv haarcascades</li>
  <li>Above filters are used to get the cropped face</li>
  <li>Features are detected using wavelet transform</li>
</ul>
<div data-testid="stBlock" width="437" class="css-140646 e1tzin5v3"><div data-testid="stHorizontalBlock" class="css-rncmk8 e1tzin5v0"><div data-testid="stBlock" class="css-1r6slb0 e1tzin5v2" style="position: relative;"><div style="overflow: visible; width: 0px;"><div data-stale="false" class="element-container css-1e5imcs e1tzin5v1" style="width: 135px;"><div class="css-o1jpvw e19lei0e1"><button title="View fullscreen" class="css-6awftf e19lei0e0"><svg viewBox="0 0 8 8" aria-hidden="true" focusable="false" fill="currentColor" xmlns="http://www.w3.org/2000/svg" color="inherit" class="e1fb0mya0 css-xq1lnh-EmotionIconBase ex0cdmw0"><path d="M0 0v4l1.5-1.5L3 4l1-1-1.5-1.5L4 0H0zm5 4L4 5l1.5 1.5L4 8h4V4L6.5 5.5 5 4z"></path></svg></button><div class="css-1kyxreq etr89bj0" style="width: 135px;"><div data-testid="stImage" class="css-1v0mbdj etr89bj1"><img src="https://politicianrecognition.herokuapp.com:443/media/ba95fe30833a674f4edb91ab2cdcdfca6629bfe35ec908c5801cbfca.jpeg" alt="0" style="max-width: 100%;"><div data-testid="caption" class="css-1c94hsa etr89bj2"> Original </div></div></div></div></div></div><div class="resize-triggers"><div class="expand-trigger"><div style="width: 136px; height: 209px;"></div></div><div class="contract-trigger"></div></div></div><div data-testid="stBlock" class="css-1r6slb0 e1tzin5v2" style="position: relative;"><div style="overflow: visible; width: 0px;"><div data-stale="false" class="element-container css-1e5imcs e1tzin5v1" style="width: 135px;"><div class="css-o1jpvw e19lei0e1"><button title="View fullscreen" class="css-6awftf e19lei0e0"><svg viewBox="0 0 8 8" aria-hidden="true" focusable="false" fill="currentColor" xmlns="http://www.w3.org/2000/svg" color="inherit" class="e1fb0mya0 css-xq1lnh-EmotionIconBase ex0cdmw0"><path d="M0 0v4l1.5-1.5L3 4l1-1-1.5-1.5L4 0H0zm5 4L4 5l1.5 1.5L4 8h4V4L6.5 5.5 5 4z"></path></svg></button><div class="css-1kyxreq etr89bj0" style="width: 135px;"><div data-testid="stImage" class="css-1v0mbdj etr89bj1"><img src="https://politicianrecognition.herokuapp.com:443/media/212fffbee018d612725e0f031cbe7f47aab966b87dfce16325472e76.jpeg" alt="0" style="max-width: 100%;"><div data-testid="caption" class="css-1c94hsa etr89bj2"> haarcascades detection </div></div></div></div></div></div><div class="resize-triggers"><div class="expand-trigger"><div style="width: 136px; height: 209px;"></div></div><div class="contract-trigger"></div></div></div><div data-testid="stBlock" class="css-1r6slb0 e1tzin5v2" style="position: relative;"><div style="overflow: visible; width: 0px;"><div data-stale="false" class="element-container css-1e5imcs e1tzin5v1" style="width: 135px;"><div class="css-o1jpvw e19lei0e1"><button title="View fullscreen" class="css-6awftf e19lei0e0"><svg viewBox="0 0 8 8" aria-hidden="true" focusable="false" fill="currentColor" xmlns="http://www.w3.org/2000/svg" color="inherit" class="e1fb0mya0 css-xq1lnh-EmotionIconBase ex0cdmw0"><path d="M0 0v4l1.5-1.5L3 4l1-1-1.5-1.5L4 0H0zm5 4L4 5l1.5 1.5L4 8h4V4L6.5 5.5 5 4z"></path></svg></button><div class="css-1kyxreq etr89bj0" style="width: 135px;"><div data-testid="stImage" class="css-1v0mbdj etr89bj1"><img src="https://politicianrecognition.herokuapp.com:443/media/4ec54faf2d84ae40d3782670df334bb992e53da4f01683c0761a396a.jpeg" alt="0" style="max-width: 100%;"><div data-testid="caption" class="css-1c94hsa etr89bj2"> wavelet transform </div></div></div></div></div></div><div class="resize-triggers"><div class="expand-trigger"><div style="width: 136px; height: 209px;"></div></div><div class="contract-trigger"></div></div></div></div></div>

* **Feature Used**: 'movie_id','title','overview','genres','keywords','cast','crew' are the features I used to create tags
* **Data Cleaning** : There were 3 movies where overview was missing so I removed these movies.Genres,keywords,cast are crew columns are list of dictionaries so I wrote some functions to extract only genre name and keyword name,top 3 actors/actresses from cast and name of the director from crew column.
* **Creating Tags**: After cleaning Genres,keywords,cast are crew columns I merged them with the overview column to create tags which will be useful when we make our model.
* **NLP preprocessing**: Then I removed html tags from tags column and converted it into lowercase.Then I tokenized it and removed english stop words and then ran stemming on it.
* **Word Embedding**: Then I used Count Vectorizer(Bag of words) to create 5000 features on 4806 movies.
* **Cosine Similarity**: On top of these 4806 vectors I ran cosine similarity to find nearest vectors and we use 10 of most similar vectors to recommend movies
* **Deployment**: Deployment is done on **heroku** using streamlit.Check out the <a href="https://movie-recommender-saqib.herokuapp.com/">demo</a> here: 
* etc.

### Technologies Used:
* Python
* Pandas,Sklearn, jupyter
* Streamlit
