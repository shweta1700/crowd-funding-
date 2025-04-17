# crowd-funding-
A blockchain  mini project for crowd funding 
Contract Crowdfunding
{
mapping (address => uint) public contributors
address public manager;
uint public minimum Contribution ;
uint public deadline;
uint public target ;
uint public raised Amount;
uint public noOfContributors;
Constructor (uint_target, uint_deadline) {target=_target;
deadline. block. timestamp +_deadlines :
minimumContribution = 100 wei;
manager = msg.sender;
}
Funtion send Eth() public payable
{
require (block timestamp < deadline “Deadline has passed");
require (msg value > = minimum Contribution "Minimum Contribution is not met”);
if (Contributor[msg.sender] == 0) {
noOfContributors ++;
}
Contributors [mag.sender) += msg. value/ 10**18 value/
raisedAmount ++= msg. value/10**18
{
Function get ContractBalance() public view returns (uint) 
{
return address(this.balance) / 10**18;
{
Function refund() public
{
require (block.timestamp> deadline && raised Amount < target,” you are not eligible for refund ");
require (Contributors[msg.sender] > 0,"you are not contributor or already refunded ");
address payableuser = payable(msg.sender);
user transfer (contributors [msg.sender]/10**18);
Contributors [ msg.sender) = 0;

struct Request{
String description;
address payable recipient;
uint value;
bool completed;
noOFVoters;
mapping (address => bool ) voters;
{
mapping (uint => Request) public  uint public numRequests,

modifier only Manager() 
{
 require (msg sender == manager " only manager can call this function"); 

Function Create Requests (string memory_description ,address payable_recipient, uint-value) public onlyManger
{
Request storage new Request = requests [num Requests];
numRequets ++;
newRequest.recipient = _recipient;
newRequest.description = _description;
newReques.value= _Value;
newReques.completed = fells
newReques.noofvoters = 0;
}
function voteRequest (uint_request NO) public 
{
require (contributors [msg.sender] >O, You must be a contributor");
Request storage this Request = requests [_requestNo];
require (this Request voters [msg.sender]==
False, "you have already voted ");
thisRequest, voters (msg.sender] = true; 
this Request noOfVoters ++;
}
Function make Payment (uint_request No) public only manger 
{
require (raiseAmount > = target);
Request storage this Request=requests [-request No];
require (this Request completed = =”The request has False been completed ");
require (this Request - noOf Voters >
noof Contributors /2" Majority does not Support”);
this Request recipient, transfer (this Request Value);
this Request completed = true; 
}

