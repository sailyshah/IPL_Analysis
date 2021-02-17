# IPL_Analysis
Cricket is a sport played by two teams with each side having eleven players. Each team is a right blend of batsmen, bowlers and allrounders. The batsmen’s role is to score maximum runs possible and the bowlers have to take maximum wickets and restrict the other team from scoring runs at the same time. Each player contributes towards the overall performance of the team by giving his best performance in each match. Each player’s performance varies with factors like the team he is playing against and the ground at which the match is being played. The performance of a player also depends on several factors like his current form, his performance against a particular team, his performance at a particular venue etc. There are various attributes that help us in players’ performance prediction in the game of cricket. Following are the measures that are deerived during exploratory data analysis of our dataset:


## A] TRADITIONAL ATTRIBUTES
As mentioned in the previous section, the statIstics of the players such as average, strike rate etc. are not available directly for each game, we calculated these attributes from the innings by innings list using aggregate functions and mathematical formulae. These attributes are generally used to measure a player’s performance. These attributes are as follows:

### 1] Batting Attributes

1.1 No. of Innings: The number of innings in which the batsman has batted till the day of the match. This attribute signifies the experience of the batsman. The more innings the batsman has played, the more experienced the player is.

1.2 Batting Average: Batting average commonly referred to as average is the average number of runs scored per innings. This attribute indicates the run scoring capability of the player. 
    
    Average = Runs Scored / Number of times dismissed

1.3 Strike Rate (SR): Strike rate is the average number of runs scored per 100 balls faced. In limited overs cricket, it is important to score runs at a fast pace. More runs scored at a slow pace is rather harmful to the team as they have a limited number of overs. This attribute indicates how quickly the batsman can score runs. 

    Strike Rate: (Runs Scored / Balls Faced) * 100

1.4 Centuries: Number of innings in which the batsman scored more than 100 runs. This attribute indicates the capability of the player to play longer innings and score more runs.

1.5 Fifties: Number of innings in which the batsman scored more than 50 (and less than 100) runs.This attribute indicates the capability of the player to play longer innings and score more runs.

1.6 Zeros: Number of innings in which the batsman was dismissed without scoring a single run. This attribute shows how many times the batsman failed to score runs, hence this being a negative factor, was impacts the batsman’s prediction negatively.

1.7 Highest Score: The highest runs scored by a batsman in any (single) innings throughout his career. This attribute is used in the formula for calculating the venue attribute. This attribute shows the run scoring capability of the batsman at the venue. If a player has s very high score at a venue in past, he is more likely to score more runs at that venue.

### 2] Bowling Attributes

2.1 No. of Innings: The number of innings in which the bowler bowled at least one ball. It represents the bowling experience of a player. The more innings the player has played, the more experienced the player is.

2.2 Overs: The number of overs bowled by a bowler.This attribute also indicates the experience of the bowler. The more overs the bowler has bowled, the more experienced the bowler is.

2.3 Bowling Average: Bowling average is the number of runs conceded by a bowler per wicket taken. This attribute indicates the capabilities of the bowler to restrict the batsmen from scoring runs and taking wickets at the same time. Lower values of bowling average indicate more capabilities. 

    Bowling Average: Number of runs conceded / Number of wickets taken

2.4 Bowling Strike Rate: Bowling strike rate is the number of balls bowled per wicket taken. This attribute indicates the wicket taking capability of the bowler. Lower values mean that the bowler is capable of taking wickets quickly. 

    Strike Rate: Number of balls bowled / Number of wickets taken

2.5 Four/Five Wicket Haul: Number of innings in which the bowler has taken more than four wickets. This attribute indicates the capability of the bowler to take more wickets in an innings. Higher the value, more capable the player.

## B] DERIVED ATTRIBUTES 
To predict a player’s performance, his past performances need to be analyzed in terms of how much experience does he have, how consistent he has been in his performance, how well he has been performing in recent matches, how well can he tackle the bowlers/batsmen of different teams, how well does he play at different venues, etc. Traditional measures of players’ performance cannot reflect these factors directly. So, we tried to reflect and quantify them by deriving four new measures from the traditional measures. These attributes are weighted averages of the traditional attributes. These attributes are explained as follows:

### 1. Consistency: This attribute describes how experienced the player is and how consistent he has been throughout his career. All the traditional attributes used in this formula are calculated over the entire career of the player.

Formula for batting: Consistency = 0.4262average + 0.2566no. of innings + 0.1510SR + 0.0787Centuries + 0.0556Fifties – 0.0328Zeros

Formula for bowling: Consistency = 0.4174no. of overs + 0.2634no. of innings + 0.1602SR + 0.0975average + 0.0615*FF

### 2. Form: Form of a player describes his performance over last one year. All the traditional attributes used in this formula are calculated over the matches played by the player in last 12 months from the day of the match.

Formula for batting: Form = 0.4262average + 0.2566no. of innings + 0.1510SR + 0.0787Centuries + 0.0556Fifties – 0.0328Zeros

Formula for bowling: Form = 0.3269no. of overs + 0.2846no. of innings + 0.1877SR + 0.1210average + 0.0798*FF

### 3. Opposition: Opposition describes a player’s performance against a particular team. All the traditional attributes used in this formula are calculated over all the matches played by the player against the opposition team in his entire career till the day of the match.

Formula for batting: Opposition = 0.4262average + 0.2566no. of innings + 0.1510SR + 0.0787Centuries + 0.0556Fifties – 0.0328Zeros

Formula for bowling: Opposition = 0.3177no. of overs + 0.3177no. of innings + 0.1933SR + 0.1465average + 0.0943*FF

## C] miscellaneous Attributes (These are Overall IPL career Attributes)

### 1. Role: The playing role of the player.

### 2. Most Sixes : Number of Sixes Scored by Each Player

### 3. Most Fours : Number of Fours Scored by Each Player

### 4. Most Dots Played : Number of Dots played by Each Player

### 5. Most Ducks : Number of times the player got out at zeroes

### 6. Fastest Fifty : What is the least number of balls taken by the player to score fifty and against which team?

### 7. Fastest Century : What is the least number of balls taken by the player to score century and against which team?

### 8. Best Partnership : Till Now with whom the player had best partnership and against which team?

### 9. Number of Not outs : Out of all the innings played by the player how many times he was not out?

### 10. Most 1's : How Many Runs a player scored in his overall IPL career by one's?

### 11. Most 2's : How Many Runs a player scored in his overall IPL career by two's?

### 12. Most 3's : How Many Runs a player scored in his overall IPL career by three's?

### 13. Overall Player Performace (OPP) : 
        OPP = Total Runs Score by the player/Number of Balls Faced + (Boundary Runs Scored(by 4's and 6's) - Non Boundary Runs Scored(by 1's,2's, 3's))/Number of Balls Faced

### 14. Dismissal Types : Bifurcating when the player got out what & his dismissal kind i.e., how he got out.?

NOTE :  I have also calculated the Player statistics on basis of Powerplay, Middle Overs and Death Overs. Please refer Notebook for detailed analysis.

Hope, you will learn a lot from this Analysis. "Any advice and suggestions will be greatly appreciated!!".

Happy Learning..!!!
